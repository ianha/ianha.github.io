---
title: Thoughts on Peer Reviewing Source Code
author: admin
layout: post
permalink: /thoughts-on-peer-reviewing-source-code/
categories:
  - software
---
Last month I attended [OSCON][1] 2012 in Portland, Oregon. OSCON is the largest open-source convention in North America. Pretty much nerd heaven, which suits me perfectly fine. While there were some hits amoung the misses, my colleague [Scott Hyndman][2] and I came away with some motivating ideas to take back to [Blu Trumpet][3].

One of those ideas is peer reviewing code. Yes, we were guilty of not reviewing code before commits. So three weeks ago we decided as a team to have every git commit be peer reviewed, as a first run. Our process works as follows:

*   commit changes as a feature branch via [git flow][4] and push the branch upstream
*   create a pull-request via github
*   randomly assign someone on the team to review the code via Campfire (this is done via [Hubot][5], our IRC robot we&#8217;ve programmed internally at BT)
*   pair program and have the commiter explain the code to the reviwer before merging

After three weeks of this, I can personally say that our code quality has improved. We are slowly getting everyone on the same page on coding style because it&#8217;s enforced during the pair programming phase. Futhermore, we are getting nice knowledge transfer across our team as the random selection forces members to familiarize themselves with different components of our system.

It has also dawned on me that peer review is a great way to refactor the code base. We often think of refactoring as a hammer job, but minor refactors over time can really clean up the code long term. We&#8217;ve taken a &#8220;always have a commit make the code base better&#8221; attitude on every merge.

But what I love most about peer review is that it *feels good*. I get a little dopamine spike every time I commit something knowing that the code style has improved and any minor refactors have taken place. This is probably it&#8217;s most powerful benefit.

You see, over time, when building a team, you want [good habits][6]. And how do you build habits? By applying a well-known pattern known to [create][7] them:

*   have a stable repeating anchor (pull-request)
*   engineer as easy an habit as possible (review the code for style and design improvements)
*   be rewarded for the habit (the good feeling I get when I know I&#8217;ve done my job)

This is precisely why peer review works. It plugs into a habit-forming routine that transfers across team members. We plan to make improvements and adjustments as we move forward, but so far it&#8217;s been a positive experience.

 [1]: http://www.oscon.com/oscon2012
 [2]: https://twitter.com/scotthyndman
 [3]: http://www.blutrumpet.com
 [4]: http://nvie.com/posts/a-successful-git-branching-model/
 [5]: http://hubot.github.com/
 [6]: http://blogs.hbr.org/cs/2012/04/in_his_classic_talks_to.html
 [7]: http://tinyhabits.com/