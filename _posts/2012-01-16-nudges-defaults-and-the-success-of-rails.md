---
title: Nudges, Defaults and the Success of Rails
author: admin
layout: post
permalink: /nudges-defaults-and-the-success-of-rails/
categories:
  - rails
  - ruby
  - software
---
Humans are lazy. You didn&#8217;t need me to tell you that. Status quo bias and inertia constantly work against our better judgement to learn and improve.

In Richard Thaler and Cass Sunstein&#8217;s fascinating book [Nudge: Improving Decisions About Health, Wealth, and Happiness][1] the two researchers explore how certain psychological triggers and observations can be used to design choices to persuade and &#8220;nudge&#8221; people to desirable behaviours. One of those observations is the use of defaults.

Default choices are a powerful but simple way to nudge behaviour. Opt-out defaults for magazine subscriptions work wonderfully, as Thaler and Sunstein point out: people continue to pay even when they stop reading. More dramatically, opt-out 401(k) company plans have more than double the savings rates than opt-in plans. When given the choice to do nothing, most will.

As a software developer, this got me thinking: What kind of defaults can I design that will nudge my users to behaviours I find desirable?

It hit me that the influence of defaults went beyond asking the question. Defaults in fact are a big reason that my professional life is easier and more enjoyable than it was before. And I have Rails to thank for that.

Rails is filled with defaults. This is one of the main reason for its success. Someone, somewhere decided that 80% of things developers deliberate on don&#8217;t matter. How to structure an application, how to setup a database, which server to test against&#8212;there are defaults for all of these and they work out-of-the box for most developers. There&#8217;s even a phrase for this: Convention over configuration.

David Heinemeier Hansson, the creator of Rails, had this to say at RailsConf 2008:

> *One of the points I keep coming back to with Ruby on Rails, is that we confess commonality. That we confess that we&#8217;re not as special as we like to believe. We confess that we&#8217;re not the only ones climbing the same mountain&#8230;I think the conclusion&#8212;the conclusion that we&#8217;re not as special and unique as we like to believe&#8212;is the fact that the flexibility we think we need, we want&#8212;we really don&#8217;t.*

By designing defaults intelligently, Rails was able to hit that sweet spot of doing as much work for you, while enabling it to get out of the way when needed. I&#8217;ve had experienced Rails developers echo this very thing. It goes to show that as something as influential as Rails, defaults can have a big impact.

 [1]: http://www.amazon.com/gp/product/014311526X?ie=UTF8&tag=nudge-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=014311526X