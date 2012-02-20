---
layout: post
title: "djax: dynamic pjax for complex layouts"
category: javascript
tags: ['pjax', 'jquery', 'ajax', 'javascript']
---
{% include JB/setup %}

I think [pjax](https://github.com/defunkt/jquery-pjax) is one of the coolest things out there, and I've been looking for excuses to use it since I first saw it on hacker news last year.

Working for a primarily WordPress based shop, I took several cracks and racked my brain trying to come up with the best way to utilize pjax to get [BostInno](http://bostinno.com) running
smooth the way only partial page loads can do. Along the way I toyed with one [WP plugin](http://wordpress.org/extend/plugins/pjax-menu/), which was good for some inspiration... and more
recently took a gander at a [theme](https://github.com/wayoutmind/thematic-pjax) approach to solving this problem.

I somehow could not reconcile with the approach, particularly for BostInno, where different sections of the layout update at different times depending on the actual page transition taking
place. And that's apart from the high number of custom page templates we use. I could not see how loading just one container on the page dynamically was going to suffice, so I went to the
drawing board.

Enter djax: by marking all of my dynamic areas with a class that I pass to my plugin, djax is able to compare only elements with this class between the current and requested page, adding
elements that don't yet exist, removing elements that no longer exist, and updating elements that have changed. If any dynamic elements are found to be identical between the two pages, they
are left completely alone, along with any non-dynamic areas on the page.

Of course it only took a bit of playing around before I realized I needed exceptions, which can be passed in as an array of url fragments to be matched against, and events, which can be heard
on the window object under the event name djaxLoad. As a convenience djaxLoad will pass an object containing the url and page title of the requested page. Overall I'm *very* pleased with how
easy this has been to use, and looking forward to seeing it up and running at Streetwise. In the meantime, you can see full usage [here](http://beezee.github.com/djax.html), download the plugin
and a working example [here](https://github.com/beezee/djax), or see a working [WP theme](http://themble.com/bones/) implemented with djax [here](http://brianzeligson.com/djax), (about [28 lines of
code](https://github.com/beezee/bones-responsive/commit/58aadde224d74f8aaa3266a4bd76e961f2888ada) to get that working...) And just in case you want to see them, the modified theme is [here](https://github.com/beezee/bones-responsive).