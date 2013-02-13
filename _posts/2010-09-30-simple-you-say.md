---
layout: post
date: 2010-09-30 19:02:00 UTC
title: Simple, you say?
---

A lot of the programming I do is around the edge cases. It's not most of what I do but it is a healthy chunk. And that is a good thing; let me explain why.

The virtues of simplicity is definitely overrated, or at the least word simple is overloaded in the sense that people use the same word when they are talking about different things and arrive at unintended conclusions.

That is not to say simple ideas are bad; a lot of great products are clearly born out of simple; Digg is just a list of links that you vote up and down, Google is just a search engine, Quora is just a search engine and iPhone is just a phone.

However, simplicity takes a lot of work. I like to think of it as a computer game; the main thing is to never let the user get themselves into a corner they can't back out of.

That requires a lot of work. Just off the top of my head, for a simple web application with a single form, you might need to consider:

- How do you show errors to users; do you have a generic notification system or do you handle cases one by one? (Answer: Both. you should try to help users as much as you can but realize that they'll manage to break things in some way you can't think so have a fall-back)
- Is there any way you can recover from the error gracefully? This has a lot of implications as you might need to keep state across pages.
- If things fail miserably, what do you? How do you both notify the user that things have failed but also keep your cool, keep the user likely to keep using stuff.

And really, this is tip of the iceberg.

However, all this hard work doesn't mean that it should be boring. Following the computer game analogy, I liken it to never crashing the game. Once you have the user on your site, you need to do your best to keep them playing without letting them ever get suck.

That's why simplicity takes a lot of work, especially on a popular product used by millions. There are definitely tools you can use such as a framework for handling errors both in the technical sense and the interaction design sense.

Think of how list views on iPhone almost all the time have a Back button on top left or the logos on top left of websites (like Digg, Twitter, Quora, Facebook) always take you to homepage, just like a reset button.

All in all, next time you look at a simple and a well executed idea, realize that big part of simplicity is to  function of how to manage errors, expectations.

TL;DR: Play more computer games.
