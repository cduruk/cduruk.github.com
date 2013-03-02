---
layout: post
date: 2012-05-19 19:02:00 UTC
title: What was it like to work at Digg during Digg V4?
---

_This is a Quora answer that I decided to move to my personal blog._

Unique.

I joined Digg pretty late in the product cycle of Digg V4. Eagle-eyed followers of Digg might have noticed that the version of Digg V4 was somewhat different than the Digg V4 that was shown around in Diggnation in SXSW 2010.

When I started at June, right out of college[1], V4 was pretty much finished feature wise and most people were tasked with actually building things up to scale and start thinking about how to launch it. As Digg V3 was actually live at the time too, there was a lot of technical work that needed to be done for moving the data and of course there were some launch-related features like the invite system. For example, my first projects were related to building the parts of invite system and supporting short URLs generated in V3 on V4.

There was definitely a lot of unknowns before launch. Every single person was ready for some sort of backlash. We knew some people would simply not like it because, as the consumer product vernacular goes, people hate change. But more than that, we knew that Digg had a very vocal user base, who rightfully believed that their contributions, their time on Digg made Digg what it was.

As nervous as people were, there was a lot of excitement for the launch. On the product side of things, Digg had been pretty stagnant for a while and there were more places where people could find and read news, like Twitter and Facebook. On the engineering side, there was a lot of effort put in to make a really scalable infrastructure using some brand-new tools and in general, a lot of things were done the right way.

Anyway, launch.

I can't remember how we exactly set the date. I think it was a combination of marking off the bugs we definitely wanted fixed and some sort of "we should get it out" for sure.

On the day of launch, we have reorganized the engineering floor (which was a silver-painted warehouse, which used to be a church though you could't tell) to have one big table and put the couches around too. There was some nice food being served, couple lights and and projectors were set up for the Twitter feeds and metrics. An hour or so ago, most of the engineers were set up so that everyone was on IRC, which remained the main form of communication at Digg, people who needed to were tailing the production logs from Scribe, the procedure for immediately triaging and assigning bugs were all discussed.

I certainly was scared as someone who did mostly front-end work so I cannot imagine how people who worked a bit lower to the ground felt like. All in all though, people were excited to see their work go live.

The few hours right after launch were tough. We did have a couple technical challenges, though probably the extent of it was a bit amplified by the press. Sure, the site worked a lot slowly than we would have liked and when it came back up, it had some trouble staying up. I will be voting along the party lines here as an engineer and I am probably diluting the technicalities of building a service like Digg at that scale as a measly front-end engineer, but once everyone good a grasp of the performance characteristics of a lot of the backend stuff, the site became reasonably stable. 

As I mentioned, people were ready for some sort of backlash and we knew the press would be watching like a hawk. There were, however, couple instances that I personally wasn't ready for. At the time, the list of employees were visible on our Team page and couple people searched for each individual's name. So I had a couple reaching out to me on my personal email and Twitter, and, errrr, express their discontent in colorful terms. It wasn't scary or annoying, just unexpected.

The most important thing right after firefighting and cleaning up some of the fallout after the launch was figuring out what the next thing would be. The driving force behind a lot of technical decisions was building a platform; the Digg website and the API all ran on Thrift services (which was super nice, in my opinion [4]). So there was the idea of building more features on top of the platform in line with the grander vision but also some pressure to bring back some of the old stuff. If I had to pick one thing, I'd say that's one thing I wasn't very excited about initially was that we've decided to bring on more of the old features.

There were a couple high profile features like the RSS imports that made a lot of users feel like they lost the ownership (which everyone knew would receive a lot of feedback) but the more interesting things were like how tons of people were upset about things like changing the things buttons on comments from Thumbs Up / Thumbs Down to arrows. I can probably count several of such seemingly small things that turned out to be *big deals*, in terms of user sentiment.

Anyway.

While all this was happening, Digg had a new CEO, whose search has long begun before the launch. Some people were excited about it, some people weren't but I think. For a lot of people, Digg meant Kevin Rose and vice versa. I was more on the side of "eh, who is this guy?" initially. I think I saw it as having a tenured CEO coming from a Big Company would soon change the workplace. That's not to say we didn't need some change but I think I wanted things to be more "fun". Ah, the young me. I couldn't be more wrong as Matt turned out to be not just a great mentor who I looked up to pick up some C-level tricks but also who is very clever, direct and a keen sense of humor.

There was the layoffs, which of course wasn't pleasant. I was lucky enough to be not laid off, considering my visa was sponsored by Digg and that could technically mean I would have to leave the country. [3] The day of layoffs, I don't think anyone did any work.

The next day, however, was the polar opposite and was probably one of the most teaching days during my time at Digg. The day after layoffs, we've all sit in a room and assigned project to people and everyone started working.

See, I think I went to work that day in all sorts of existential thoughts in my head, contemplating whether or not I should stick this one out or just go back to Turkey or maybe find another job or something else. I knew there would be shit ton of press that I could probably spend the entire day reading. I had long since removed Twitter from my computer as I knew it'd be nothing but a source of misery.

However, 40 minutes into that day, I had a project assigned to me and I was working. To this day, I remember the day after the layoffs as the day where I learned how once you are excited and have a goal to strive towards, none of the other crap matters.  More eloquently, "focus or die".

Soon after the layoffs, there was a considerable paradigm shift and honestly, productivity went up. Part of is was definitely the significantly shrinker overhead; it was easier to just push the code to production and individual teams, whose sizes went from 6-7 to 2-3 at most, were more empowered. There was also the other part which was that people who had stayed kind of felt like it was now on them to turn things around. 

As the team size went down, the engineering team moved to the other part of the Digg HQ --we were separated between 2 floors of the SF Guardian Building and the warehouse-church the engineering building--. It felt less like a hacker warehouse but it was actually a really nice office space and had actual windows.

My memory goes a bit less vibrant as I think further. As a much smaller team, we have worked on a lot of different features and I certainly felt like I was very empowered.

As days passed by, I personally have risen up in the company and had a lot more say, even on the executive level. Everyone believed in the original mission of Digg, I felt like, which was getting people the news they cared about. Digg, for me and many others, was never about the digg counts or the subculture it created. Both were extremely essential, for sure, but I think I always looked at them as tools to get people to the news they cared about. 

For me, I knew it was time for me to try something different was the way I believed on how to do that wasn't the way others wanted to do that.

From what I could tell Digg didn't really have a lot of pressure from the VCs to do this or that but internally, everyone wanted to move the needles up. Digg had a lot of technical assets, brand recognition and the talent to execute on many of the ideas.

So, I have argued rather colorfully with a lot of the executives on why I didn't want to work on the upcoming projects as I believed they'd distract us from what I believed were the right things.

On top of that, couple of the people I was working very closely with had left and I was interested in working at a different kind of a company made me soon leave. People knew as much as I did that I'd not be very happy and productive working on some of the new stuff so everyone understood. As I am on a visa and changing jobs is an ordeal while on one, everyone again went out of their way to accommodate me more than the usual 2 weeks just to make sure I am never in a legal gray area.

This answer became way longer than I imagined and I am very slightly tearing up as I am writing these. I have teared up many times talking about Digg (or even at Digg). At the end of it all, it was my first real job outside of college. There were times I felt miserable enough to just leave work at 4 and ride my bike for hours (which did help me lose a lot of weight) and other times where I was scared to death about how much responsibility I was given on a site had millions of people visiting.

I haven't had a lot of jobs so I can't reasonably judge but I can't imagine being at Digg before, during or after V4 launch being the easiest job. Technical challenges were huge, and dealing with an extremely vocal user base who are almost as invested in the product as you are while taking shit from the press left and right was pretty taxing. But you know, everyone loves drama and pretty much everyone loves to watch Rome burn. I personally enjoy bitter chocolate.

V4 was a different product than anything else out there and had it worked as we've liked, it'd have been an astounding success story. It didn't. But that's fine. Digg pushed on, and even invented, some of concepts that we take for granted now like those sharing buttons, building communities across many different interests. It pioneered technologies, contributed heavily to open source, created not a subculture on the internet but also a very open and fun culture among its employees also.

I feel damn lucky I got to be part of a special company like Digg at a very special time.

1: It was almost too right out of college. Before preparing my offer letter, they asked me when I was graduating and I put in May 16, as that was the day I was getting my diploma. And the start date on my offer letter turned out to be May 17. Due to the sheer excitement of getting a job at Digg, I didn't really notice that, until I was getting my plane tickets. I called up the office, told them that I really couldn't move across the country in a day. Fortunately, they were more than understanding --though they did push from the month I wanted to 2 weeks--.

2: Digg V3 and V4 technically shared no code, they were entirely separate projects with V3 being all in PHP + MySQL and V4 being a brand-new PHP app running on Python (and very little Java) services on Cassandra and Redis. I did actually copy-paste 20 or so lines of advertising cookie from V3.

3: In reality, had I been laid off, I had a feeling that they would go out of their way to make sure I wouldn't actually get kicked out of the country. One common theme among all the sensitive issues at Digg, the management always went out of their way to help the employees or even the former ones out.

4: To give perspective, I had my laptop set up done in less than half a day and submitted a code for review before I left work that day. I was also really big fan of how our deployment worked. In general, shit ton of operational magic just worked.