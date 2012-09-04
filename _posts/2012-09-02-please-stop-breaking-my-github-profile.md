---
layout: post
title: "Please stop breaking my github profile"
category: Development
tags: ['anti-patterns']
---
{% include JB/setup %}

###Update

Thanks to [coverband](https://github.com/coverband) and [David Coallier](https://github.com/davidcoallier) for
[promptly addressing this](https://github.com/resume/resume.github.com/pull/41).

###tl;dr - If you're going to scrape my data, make sure your error messages don't blame _me_ when something goes wrong.

Right now the [top story](http://news.ycombinator.com/item?id=4466883) on hackernews is a link to a clever project that uses
the github api to build a resume from your profile.

It's actually a nice way to view a github profile, here's a glimpse of what [my link](http://resume.github.com/?beezee)
looks like in Firefox:

<img src="/assets/images/gr_good.png" height='300px' width='400px' />

The problem arises when I load the same page up in Chrome (running latest version on Ubuntu)

<img src="/assets/images/gr_bad.png" />

###This error message blames _me_.

Let's imagine for a moment that a friend of mine recommends me for a position that pays 7 figures. The hiring manager happens to
prefer the presentation of a github resume, and also happens to be really busy. She points her browser to http://resume.github.com/?beezee
and sees 

>"We couldn't find enough to build a resume from."

What does a busy hiring manager think when looking at this message? _This guy has nothing to show. Moving on..._

There goes my 7 figure salary, thanks alot.

I never asked to have a github resume, and I can't opt out, so at least if you encounter an error, take responsibility for it. Here's
a less offensive option:

<img src="/assets/images/gr_better.png" />

Even better would be to redirect straight to my github profile.

If your app is going to represent people (especially without their consent,) please be responsible and take ownership of problems
that occur in your code.

