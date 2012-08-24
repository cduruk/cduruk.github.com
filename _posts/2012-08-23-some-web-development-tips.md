---
layout: post
date: 2012-08-23 21:00:00 UTC
title: Some Web Development Tips
---

This is a relatively random and unorganized set of web development tips that I derived from a set of interview questions I created when I worked at Digg, which in turn was derived from my personal set of notes that I collected as learned and figured out things. The language is intentionally informal and I doubt it will ever change, unless it causes some ambiguity. While most of the tips represent best practicses, some of them are more focused on developer productivity or sanity maintenance at the cost of best practices.

Most likely, a lot of the tips here don't apply to your situation; Digg was a relatively high trafficked website, had its own PHP and JavaScript frameworks (which were necessary to due to our performance requirements) and a lot of the things here are pretty easily taken care of by just using a framework like Rails, Django, or Pyramid.

While I was the person responsible for a lot of Digg's front-end for a while (much to my amazement), these tips don't represent Digg's general approach. Please take these more as a set of guidelines or even a braindump of a single web developer who had to learn a lot on the job.

I am hoping to keep this list as _my_ canonical list of web development tips and keep it up to as date.

## Security

&middot; Unless you are using a framework, you are most likely not protecting yourself against things like CSRF attacks. Especially your AJAX requests are probably not secure. Learn and love `$.ajaxSetup` so that you can your include your CSRF tokens by default.

&middot; Know why it's important that your GET requests should always be idempotent. For example, your sign-out should only work as a POST request so that someone cannot make your users sign out by just including an `<img>` tag in their forum signature.

## Performance

&middot; Sprite assets. It's worth the effort but make it effortless anyway.

&middot; Gzip all the things.

&middot; [ImageOptim](http://imageoptim.com) is awesome. You might mess up your PNGs in way that make them somewhat unusable in Photoshop._This is apparently fixed in Photoshop CS6_.

&middot; In general, reducing the number of requests made is the single biggest performance trick. _Of all the things listed here, this is probably the least relevant now._

&middot; Dealing with CDNs is a pain and they will definitely cache things in the most inoppurtine ways. Make sure your build process is smart enough to include things like CSS assets with appropriate query parameters based on your revision version.

&middot; Trying to load JavaScript dynamically is a good idea but a lot of the time, it's not worth the effort if you can keep your JavaScript to a sensible size and load it all at once. This also helps with consequent page visits being fast.

## Usability

&middot; One of the first things you should design in a AJAXy website is a unified notification system. This becomes extremely important when you do everything with an AJAX request and they fail left and right. Always notify the user when something fails; your notification system should have sane defaults.

&middot; The worst thing you can do is have a layout that requires JavaScript to be rendered. It's just bad to serve something to users and have them look at a blank screen.

&middot; Similarly, if your page renders unredably bad without CSS, your DOM is busted. Your DOM order should loosely reflect the way user reads the page.

&middot; It's in general better to not rely on a crazy hack to make a crazy layout work.

&middot; Try not to include any resource strings (like error messages or anything that will have to be translated) in your JavaScript. You should always keep them unified in a single location anyway.

&middot; Storing user preferences in cookies is a good idea until it's not. Might be worth it for short-lived features but soon enough you'll get a user who is rightfully angry that his preferences won't stick.

&middot; If any of your forms don't submit on hitting `Enter` on keyboard, you should fix them because you'll immediately get some angry user emails. Make sure you test these on browsers because the rules differ a lot.

&middot; In general don't rely on hover or scrolling for anything essential as they don't work the same way on mobile browsers.

&middot; For example, scroll events fire only after the scroll has finished on mobile browsers and there are more complications even on desktop browsers due to inertial scrolling.

&middot; If your objects change size on hover, your CSS-fu is bad and you should feel bad.

## JavaScript

&middot; Know how to read jQuery's source code if you are using it. You will most definitely run into a weird issue that will require you to do so.

&middot; For example, know that jQuery will cache `data-x` attributes internally so you won't see them update in DOM. Or that it will do different things to your AJAX request headers based on what method (`$.ajax` vs. `$.get`) you use.

&middot; jQuery plug-ins are a hit or miss.

&middot; Users have this tendency to double-click on things that they shouldn't, like submitting forms or, say, using buttons that record votes on a user-submitted news site.

&middot; In general, aim for the least amount of JS possible. This is mostly because testing JS programmatically is hard, especially in a browser environment. Selenium is a great tool in theory but your tests will rot and become useless the second you stop maintaing them, which is earlier than you think.

&middot; Sending JSON encoded HTML is easier and most of the time, fast enough. This both allows you to have less JavaScript since you don't have to bother rendering things on the client but just insert some DOMified strings into the page but also makes it easier to maintain a single set of templates.

&middot; Always return some formatted JSON from your endpoints. In general, you'll always want two parameters to be present; something that represents if the request was succesful and a payload, like your JSON-encoded HTML. Tie that success parameter to your notification system so that if a failed request isn't handled by your code, your notification system picks it up.

&middot; `==` is bad. Don't ever use it. On everything else about the language, you'll run into differing opinions.

&middot; Dealing with DOM is expensive. If you have to, use `data-x` attributes. For anything that is not DOM related, like the user name of the logged in user, keep them in JavaScript, under your own namespace.

&middot; External scripts, like those used to serve ads, will sometimes include some `document.write`s in them which might cause horrible issues like your page just going white. One way to fix it is to replace the `document.write` method in your base JavaScript. You probably should never use it anyway.

&middot; Mobile WebKit have this 300ms delay on firing `click` events after a tap. And if you have a `hover` state on anything, they will fire that on your first `tap`, requiring you to tap twice for a `click`. One way to fix it is to listen for `touchend` but be careful as that method might also fire with regular swiping.

## General Tips

&middot; Make sure your staging environment is as close to your production environment as possible. Whatever is different between those two will eventually bite you in the ass by hiding a costly bug.

&middot; For example, if you aren't serving minified JavaScript in staging, you'll definitely run into a bug where your compiled JS isn't working the same way as your non-compiled version. Don't assume minification or compilation won't change your JavaScript.

&middot; Counts are hard. Pagination is harder. Therefore, don't show counts on pagination. Flawless logic.

&middot; [Cool URIs don't change](http://www.w3.org/Provider/Style/URI).

&middot; Namespacing your AJAX endpoints under `/ajax` turns out to be great idea if you want to exclude bots or similar but it's not RESTful. Oh well.

&middot; Sooner or later, you'll end up including a some server information like your revision version, server IP, render time in a hidden comment in your HTML. Make sure you have a way to transfer that information all the way up to your templating system.

&middot; All template engines suck one way or another. Pick your battles. Try to pick something that allows you to make some sort of arbitrary coding in it  but easy access to things like your models are bad.

&middot; In general, don't rely on referer headers to be accurate for anything important. Some server in the cacaphony of your infrastructure will mess them up.

&middot; PHPLint is pretty awesome. `extract` sucks. Really, wtf?