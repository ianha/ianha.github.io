---
title: How We Built a HackTO Winning App
author: admin
layout: post
permalink: /how-we-built-an-hackto-winning-app/
categories:
  - software
---
[<img class="aligncenter size-medium wp-image-126" title="hackto2" src="http://ianha.com/wp-content/uploads/2012/04/hackto2-300x300.jpg" alt="HackTO with Team Blu Trumpet" width="300" height="300" />][1]

Yesterday, I took part along with my awesome teamates [Scott Hyndman][2] and [Victor Mota][3], in HackTO&#8217;s April 2012 hackathon as part of the Canada-wide [HackDays][4]. We had a great time thinking through the problems and the day was a lot of fun. To boot, our entry [LastResort][5] ended up placing first! We all agreed before the winners were announced that the day was a success regardless, but it was a nice icing on the cake. There were a lot of great apps.

After talking with the judges and our own observations about our approach and seeing the other 22 demos, our team brainstormed possible reasons why we placed higher than expected. Here&#8217;s what we came up with.

**Do your homework**

In a hackathon, it&#8217;s all about execution. You don&#8217;t have time. Non-demoable apps do not make the final cut, so it was crucial we knew what we were getting into before the event.

That&#8217;s why the week prior our team sat down to scope possible ideas. We familiarized ourselves with the APIs to get a feel for their range and capabilities. We even played with some of the APIs, making calls and playing with sandbox tokens. You don&#8217;t want to waste your time with mundane issues like OAuth that slow you down.

**Choose your problem carefully**

As mentioned, incomplete apps don&#8217;t demo. We made sure we had a problem that was interesting and could be done in seven hours. A completed, less glamorous app is better than an unfinished, ambitious project.

After much discussion, we settled on the following problem: A tool that monitors your existing email stream for critical issues and calls the appropriate support people by phone who can fix them.

The problem had several benefits: it scratched our own itch, so we knew it was useful (utility brownie points); it could be completed in seven hours; we double-checked the APIs were capable of doing what we wanted; and it had the bonus of using more than one of the sponsored APIs ([ContextIO][6] for email mining and [Twilio][7] for phone calls, both *awesome* APIs)&#8211;which we learned afterward one of the judges appreciated.

**Scope the day&#8217;s work**

Once we had a problem, we scoped out an MVP (Minimum Viable Product) the day before. What is the absolute minimum, demonstratable demo? We decided it was phoning a list of contacts in sequence when a specified email was sent.  That&#8217;s it. On the actual day, we hardcoded the contact list and the email was triggered by a manual send during the demo. There was no special phone call behaviour. (You can easily see how features can be added, but again the goal is brevity and speed of execution to the demo.)

We built a mantra on the team: &#8220;Build to the MVP.&#8221; Anything that sidetracked us was thrown out. It gave our team focus. We knew what the goal was.

We also wrote out the actual tasks we would need to build: github setup, necessary API keys, etc. Then we assigned a team member to each task or component. Again, we made sure items contributed to the MVP. We also made a list of &#8220;nice-to-haves&#8221; of additional features that we could add on but weren&#8217;t critical to the MVP. In the end, we didn&#8217;t implement anything off this latter list.

Why did this work? Because everyone on the team knew *exactly* what they were doing, why they were doing it, and how it all contributed to the end goal. Most importantly, each of us knew what we *didn&#8217;t* need to do, and many times we found ourselves rejecting tasks before getting sucked into time wasting.

**Choose a good team**

This goes without saying. Scott and I work together at [Blu Trumpet][8] and Victor was one of our previous interns. We all like and respect each other and know our strengths and weaknesses. We also have the added benefit of being candid and critical and there was plenty of healthy discussions throughout the day. We were constantly talking with each other, pair programming at times, pitching to help whenever. &#8220;Hey, what do you guys think of this? How does this look?&#8221; was a common phrase. We were constantly checking in on each other.

We were especially vocal during our presentation prep. We constantly asked ourselves &#8220;Is this clear? Can we make this shorter? Can we make this more impactful?&#8221; We were quick to point out when one of us was using too many words or when key points were lost. It helped a ton.

It&#8217;s next to impossible to churn something out with random people you met that day. What&#8217;s true in business is true at hackathons.

**Present as if you are pitching to VCs**

We made sure we completed at least one hour before the 5pm deadline. Why? We knew a compelling pitch was critical so we left time for it. How you present your product is really, really important. How people perceive your product *is* the product. Good impressions go a long way.

We put together a three slide Keynote presentation that made sure we (1) defined the problem and explained why it was important to solve it (server downtime is bad bad bad); (2) which audience or &#8220;customer segment&#8221; our solution served (bootstrapped startups); (3) what our value-adds were (free, developer-friendly).

We spent the final hour going over and over our presentation, timing each time. We couldn&#8217;t afford to not finish. This saved the presentation, as a final decision to shorten the demo allowed us to finish exactly in three minutes, without a second to spare (literally).

We also added humour and that never hurts! It was truly a team presentation as Victor and I did the actual presenting while Scott worked the slides and executed the demo.

**One final note&#8230;**

Writing this now everything seems &#8220;obvious.&#8221; But believe me, we were very close to not finishing. A server failure or API hangup would have cost us and put the whole thing into doubt. My heart was pounding during the presentation and thank goodness everything went as planned. Afterward, we were all surprised how nicely it all came together, as in software this rarely happens!

It&#8217;s amazing what you can accomplish in one day. Obviously, you can&#8217;t work at this speed everyday. But it was fun participating in a &#8220;mini-startup&#8221; from end-to-end. And for those thinking of working in the startup world, I highly recommend it.

 [1]: http://ianha.com/wp-content/uploads/2012/04/hackto2.jpg
 [2]: https://twitter.com/#!/scotthyndman
 [3]: https://twitter.com/#!/vimota
 [4]: http://hackdays.ca/2012/04/hackto-second-edition/
 [5]: https://github.com/ianha/LastResort
 [6]: http://context.io
 [7]: http://twilio.com
 [8]: http://www.blutrumpet.com