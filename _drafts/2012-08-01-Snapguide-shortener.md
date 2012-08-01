Sharing is right there in Snapguide's tagline; "Share what you love doing". 
Therefore, there are a lot of ways for someone to share something on Snapguide.
We knew the only we could make our sharing experience better is if we measured
and tracked how people shared content on Snapguide.

Moreover, we also wanted to make sure we could carefully account for all the
traffic our website was getting through non-browser clients that do not
properly have referer information, collectively known as Twitter clients.

Significant chunk of the Snapguide URLs we release into the wild are from our
own short domain: `http://snp.gd`. Whenever a guide is published, we
automatically create a short hash that maps to a certain guide. However, instead
of just appending that hash to our short URL, we prepend that hash with a 
alphanumeric character of our choosing. So the URL we generate becomes
`http://snp.gd/xfoobar` instead of just `http://snp.gd/foobar`. We use that
extra character to encode the data we need to track the share.

There are of course couple layers that work in unison but there is very little
if any magic involved.

When a request like `http://snp.gd/xfoobar` comes into our servers; the first
thing our nginx proxies do is rewrite it to be of the form 
`http://snp.gd/short/xfoobar` and then pass it on to our Pyramid application. 
We add the `/short` as a path so that our Pyramid app can match that URL
unambigiously via the following route: 

    conf.add_route('guide.short', '/short/{key}')

In our view callable (Pyramid equivalent of Rails actions), we parse
this `key`; the first character is the share tracking code while the rest is
the hash that maps to a certain guide.

    @view.view_config(route_name='guide.short')
    def short(self):
        req = self._request
        # The first character from a shortened URL is a source code.
        source_code = req.matchdict['key'][:1]
        hash = req.matchdict['key'][1:]

        guide_url = shortener.guide_url_by_key(hash)
        result = shortener.add_utm(guide_url, source_code)
        return httpexceptions.HTTPMovedPermanently(location=result)

The only interesting bit happens at the `shortener.add_utm` method. Here is
a simplified version of it, in all its glory.

    def add_utm(url, source_code):
        utm_map = dict(
            a=dict(
                utm_campaign='short', utm_source='email', utm_medium='email'),
            b=dict(
                utm_campaign='short', utm_source='twitter', utm_medium='web')
            ## 
            ## ...
            ##
            z = dict(
                utm_campaign='short', utm_source='foo', utm_medium='bar')
          if source_code in utm_map:
            q = urllib.urlencode(utm_map[source_code])
            return '%s?%s' % (url, q)
          return url

In essence, a request made to 'http://snp.gd/ba27r6' is served to the
users' browser as `http://snapguide.com/guides/some-guide/?utm_campaign=\
short&utm_medium=web&utm_source=twitter`. 
While it is not the cleanest URL, the added UTM parameters are automatically 
picked up Google Analytics which allows us to measure and track the shares.
Win-win!

Eagle-eyed readers might note that adding UTM parameters to a guide URL means
that we are actually serving the same content on a lot of different URLs, which
is less than ideal. Since we want to be well-mannered internet citizens and not
confuse search engines and some social network share buttons, we always include
the canonical version of the URL in our head.

    <link rel="canonical" href="//snapguide.com/guides/some-guide/" />

Encoding some metadata in a short URL is hardly a unique idea and our
implementation is yet far from perfect. However, in its current state it allowed
us to quickly get a good a insight as to how and when our guides are being
shared using the tools we have already been using.