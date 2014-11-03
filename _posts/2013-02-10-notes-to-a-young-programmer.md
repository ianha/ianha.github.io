---
title: Notes To A Young Programmer
author: admin
layout: post
permalink: /notes-to-a-young-programmer/
categories:
  - design
  - software
---
It makes me laugh to think of the code I wrote back in my early undergraduate days. How bad it was. A jumble of spaghetti without sound design principles. Ugly.

I&#8217;ve learned a lot since then, having worked professionally for some years now. For all the varied experiences from walking up at 5 AM every morning in a snowy, miserable February to finish a deadline, to help grow a startup from a handful of sever machines to several dozen, you start to see patterns. (Not to mention plenty of mistakes and failures along the way.)

Here is a list of &#8220;big picture&#8221; patterns I&#8217;ve come to understand in software development. This isn&#8217;t a commandement. It&#8217;s a personal take on what I believe matters for both individuals and teams looking to build products. It&#8217;s the list I wish I knew when I was starting out when spaghetti code was all I knew.

**Find a mentor**

The absolute best way to learn anything, in my experience, is to find someone who&#8217;s already good at the thing you want to get good at. Programming is no different. This is by far the one thing that, if you can do it, will accelerate your learning above all else.

Why? Because that&#8217;s how humans learn. Humans learn best by watching, observing and mimicking the behaviour of those around them. It&#8217;s like a shortcut. Being with a master let&#8217;s you see what&#8217;s important, the kind of questions they ask. It helps tremendously if you can have some of that &#8220;rub off&#8221; on you. Their attitude.

Luckily at work I&#8217;m surrounded by awesome programmers. I learn from them every day. I see how they use the command line. I pay attention to how they design code. If you can, find a mentor or place of work where you are close to great people. I can&#8217;t stress this enough.

I wish in my early career I payed more attention to this. So my advice: Make sure your first job or internship is at a place with great people.

**It&#8217;s about humans, not &#8220;code&#8221;**

I once got into an argument with some startup founders who asked for my help. The development lasted several months. Near the end, I told them our team in Indian wasn&#8217;t up to snuff and that we should have hired someone local to build the perfect product. Looking back, it was knee-jerk and wrong.

You see, starting engineers see code as a kind of Platonic creation. They think of the &#8220;perfect&#8221; solution to the problem if time and resources don&#8217;t matter. I know, because I was one of those people. And in that moment with the founders, I used that belief against them: Our problems would be solved if we had better written code.

<span style="font-size: 13px;">But we aren&#8217;t in the business of writing perfect solutions. Software developers are in the business of </span><a style="font-size: 13px;" href="http://www.codinghorror.com/blog/2007/09/can-your-team-pass-the-elevator-test.html">building solutions for real people</a><span style="font-size: 13px;">. </span>

Software is a just the medium. You wouldn&#8217;t say the physical sound and vibration of a guitar string is the point of music? We want to build something impactful and that only makes sense when you are building things that help actual, real people.

It&#8217;s vitally important for software developers to keep that top of mind. It keeps them&#8211;like I did with the startup founders&#8211;from jumping to &#8220;religious&#8221; viewpoints. I&#8217;ve found my skills of balancing business and customer needs with the act of software creation increasingly important. Does this feature make sense? Do our customers want it? Will it drive the business in the right directon? Given market conditions, do we have the time and money to do it? [The 10x return comes from doing the right thing, not the wrong thing well][1].

**Strive for simplicity**

A corollary from above: Write code for people, not machines. This means solving the problem at hand, of course, but it also means making it understandable to others. And the best way to do this, I&#8217;ve found, is making things simple. Brevity is a virtue.

Recently, my team was in the thick of a major redesign. The first draft was sketched on a whiteboard. It had a lot of moving parts&#8211;circles and arrows abounded&#8211;but then again we needed to scale it out and we couldn&#8217;t avoid it. Or could we? Could something simpler do the job just as well? It wasn&#8217;t clear.

In a three hour session, we discussed and dissected our assumptions, seeing what was vital or things we could push to later. In the end, a layer collapsed to a single module and we introduced a new idea that would have otherwise complicated our business logic. (Thanks Angelo!) We also decided against a cache, since we could get away with it.

By meeting&#8217;s end we understood the system and saw how it worked. Simplifications at the design level are big wins because they reduce overall maintenance and errors while boosting readability. Time and again the KISS (Keep It Simple Stupid) principle payed dividends.

Which leads to the last point&#8230;

**Don&#8217;t take the first option**

Simplicity takes work. It doesn&#8217;t just happen. We got to our design by *iterating*. Your first idea is almost never the best choice. Don&#8217;t take the first option.

In a way, this is what design *is:* It&#8217;s a process of coming to a problem today, tomorrow, the day-after-tomorrow, pruning and pruning. It&#8217;s about editing. As Steve Jobs remarked, design isn&#8217;t about how something looks, it&#8217;s how it *works*. And to understand how something works means coming to the problem again and again.

 [1]: http://www.wired.com/business/2013/01/ff-qa-larry-page/all/