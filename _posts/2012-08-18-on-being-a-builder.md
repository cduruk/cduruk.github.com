---
layout: post
date: 2012-08-18 21:00:00 UTC
title: On Being a Builder
---

One of the recurring themes in any technical team is the tension between designers and developers. Many designers complain about how their beautifully designed and well-thought out mocks aren't faithfully implemented but merely considered as guidelines. A lot of the time, the design details takes a back seat to the ease-of-implementation and how detail-oriented the developer is. While there are a lot of developers who don't mind going the extra mile to get the design "just right", most of the time, the result ends up less than satisfactory to the designer.

On the flip side of the coin, a lot of the developers complain about the seeming disconnect of designers from the realities of building an application. Sometimes this happens in the form of designer designing something that can take an inordinate amount of time to implement or simply impossible. Other times, while the design looks great on the mocks where every piece of data is the way it is supposed to be, when the design is built and tested against real-world data, it just breaks down in unexpected ways and has to change dramatically.

While I have been mostly been on the developer side of this conundrum and definitely did my fair share of my complaining, it's clear that this is a common problem with a lot of negative effects like inferior products that don't feel right, unnecessary tensions between designers and developers, and wasted iteration cycles.

Different companies seem to be attacking this problem in different ways; some companies require their "designers" to actually code their designs, with Quora being the one of the well-known proponent of that approach. Quora's job description for their product designer position explicitly lists "[Ability to build what you design](http://www.quora.com/jobs/product-designer)" amd their product designer [Anne Halsall's answer on the topic](http://www.quora.com/Quora-Product-Design/What-are-the-skills-qualities-and-background-that-I-will-need-to-get-a-job-at-Quora-or-to-work-as-a-designer-at-Quora/answer/Anne-K.-Halsall) pretty much argues that the most important thing is being a builder.. Similarly, 37signals' David Heinemer Hansson notes in a blog post that "[all 37signals designers work directly with HTML and CSS](http://37signals.com/svn/posts/1066-web-designers-should-do-their-own-htmlcss)".

Yet another approach seems to be the rise of the "front-end engineer" position. As more business and consumer applications that were once desktop applications are built as web-applications where the meat of the interaction happens in the browser, people who were once simply considered "webmasters" have rightfully claimed their titles as real developers and became front-end engineers. While this position is generally considered an engineering position, it's also always assumed (and implied in the job descriptions) that these people will have strong design sense, attention to detail to bring those intricate designs to reality as faithfully as possible.

I think both of these approaches, which aren't mutually exclusive, are valid and have their uses. Especially in a sizable organization where there are tens or hundreds of people working together, some extreme specialization is not only desired but almost required to make sure people can work without stepping on each others' toes.

However, I think the distinction between those who design and build application is an arbitrary one that is one that is slowly eroding. As there are better abstractions are built, the barrier to entry for realizing your idea and sharing it with the world becomes much, much lower. For developers, this means that they can prototype things out much faster and iterate on things themselves.

The real benefit, of course, is for the designers. For them, this means that they can just build what they had in mind without having to convince or wait for someone else to do it for them. I believe this is a game-changing freedom and it will only get better from here.

As we keep building better frameworks that encapsulate years of decision making, abstractions that hide things under the hood under under another plastic cover, and have simply better tools to get our work done, more and more people will be empowered to do things that once were within the technical reach of the few.

Today, anyone who can open up a Terminal window and [type](http://guides.rubyonrails.org/getting_started.html#creating-a-resource) `rails generate scaffold Post name:string title:string content:text` can have a very basic blog up and running in less than a couple minutes. Top this off with some Heroku action and you have a live site running on a real database on a server somewhere in a minutes.

While the iOS space is a lot younger than the web and its reach is a lot less limited, better tools and abstractions that lower the barrier of entry are coming up fast. The XCode 4 interface is a huge improvement over the XCode 3 interface that make building an app require interacting with 1 app instead of 2; story boards are making building basic, brochure like applications essentially a drag-drop exercise, appearance proxies and callback based animations are making building iOS apps feel a bit more like using stylesheets and those familiar jQuery animations. For those who are more adventerous, tools like [Pixate](http://www.pixate.com/) and [RubyMotion](http://www.rubymotion.com/) are taking the abstraction to a whole new level where building an iOS app is essentially no different than building a web app.

Discussing the pros and cons of using abstractions over specialized tools is beyond the scope of this essay; I think while abstractions built in the name of cranking out more products faster result in subpar products, abstractions and frameworks that come out of real-world needs end up getting real traction.

Essentially, I believe we are moving to a world where we will see more builders like [Sam Soffes](http://samsoff.es/) who can churn out an [iPhone app](https://cheddarapp.com/), a web application and an externally available API all by himself. When a single person can both "design" and "build" an entire product by himself, it's clear that our nomenclature hasn't fully caught up with people's newly-found abilities.

That is not to say we should abolish all specialized tools; I think there will always be need for going really under the hood and actually replacing some carburetors but today, it is possible to push that need a lot further down the line. Similarly, that is not to say there's never going to be designers who will be working away from technical tools; establishing a brand and visual identity will continue to be a job that requires professionals. Nevertheless, I believe the role of a designer as as it stands will change.

I think a lot of the responsibility will lie with the designers who will be expected to comfortable with the technology they are working with. While this seems like an exact opposite of the argument I am making, it will be more due to the adjusted expectations. Just like we are expecting better times from our Olympic athletes, designers will be expected to simply do a bit more.

As for developers, they will be freed from working as pure implementors of other people's ideas but instead work on things that they find exciting. It is hard to make a general statement as to what this could be as it's very domain specific but in general, I think in the future a lot more development effort will be focused on both building better abstractions for those who build on them and solving brand-new problems such as personalization and mining huge amounts of data.

It is an exciting time to be working in the tech industry right now. As we have built ourselves better tools, it is getting easier to simply work on the problems themselves. We'll all have to learn a couple new tricks but hey, to me, that's a small price to pay for progress.

<div class="outro">
	<p>
		Parts of this essay are inspired by Kyle Neath's <a href="http://warpspire.com/talks/chooseyouradventure/">Choose Your Adventure!</a> presentation and Clay Allsopp's <a href="http://clayallsopp.com/posts/the-shape-of-mobile-development-to-come/">The Shape Of Mobile Development To Come</a> essays. Keep on keeping on. 
	</p>
</div>