We wanted to be able to track how people share guides on social networks such as
Twitter, Facebook, and Pinterest as  well as via email. We not only wanted to 
track the social network the guide was  shared on, we also wanted to know where
the share has originated; be it our iPhone app, our website, or through one of
our Twitter accounts that tweet about new guides.

Significant chunk of the Snapguide URLs we release into the wild are from our
own short domain: `http://snp.gd`. Whenever a guide is published, we
automatically create a short hash that maps to a certain guide. However, instead
of just appending that hash to our short URL, we prepend that hash with a 
alphanumeric character of our choosing. So the URL we generate becomes
`http://snp.gd/xfoobar` instead of just `http://snp.gd/foobar`. We use that
extra character to encode the data we need to track the share.

There are of course couple layers that interact here but there's very little
magic; just using the tools and standards the way they were intended to be used.

When a `http://snp.gd/xfoobar` request comes into our servers; our nginx proxies
rewrite the URL to be `http://snp.gd/short/foobar` and forward it to
our Pyramid application; which has the following route configuration:
  
    # Pyramid configuration.
    conf.add_route('guide.short', '/short/{key}')

In our view callable (which are known as actions in the Rails world), we parse
out the `key`; the first character is the share tracking code while the rest is
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