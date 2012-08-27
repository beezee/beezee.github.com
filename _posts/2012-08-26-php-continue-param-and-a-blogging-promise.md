---
layout: post
title: "PHP continue param and a blogging promise"
category: 'PHP'
tags: ['terse code']
---
{% include JB/setup %}

I'm setting a personal goal to post something every day. No promises on quality, or content,
but something, no matter what.

Today I spent some time trying to wrap my head around [phpgolf](http://www.phpgolf.org/tips)

Looking at the higher ranked submissions for public challenges are less than helpful, people are
encoding their stuff in some way I can't even make sense of. The tips page linked above offered
some cool food for thought though.

Particularly, I found myself trying to understand this snippet that prints all primes below 1000:

    <?for($a=array(),$b=1;++$b<=1000;){foreach($a as$c)continue($b%$c?0:2);$a[]=$b;echo"\n".$b;}
    
The biggest thing that stuck out at me here was the use of continue(0) || continue(2)

I'm typically a big fan of using ternary to limit conditional logic, and setting up the environment
at the top of a block of logic so the same lines of code can be run every time. I find this much
easier to read than having to skip blocks based on the evaluation of a conditional check.
I expect to be using more of this:

    <?php
    
        foreach($a as $b)
        {
            continue($b === 'skip this'?0:1);
            //iterate
        }
        
Over what I've been doing:

    <?php
    
        foreach($a as $b)
        {
            if ($b === 'skip this') continue;
            //iterate
        }
        
Up front seems like not much different, but that's how using ternary conditionals felt at first too,
and in the end that small move grew into a major maturation of my code style, as I expect this
will.

Also nice to know you can continue more than one layer of loops by passing a higher # than 1
to [continue](http://php.net/manual/en/control-structures.continue.php), even though nested loops
are kind of smelly.

Another cool little trick I picked up on from a
[reddit r/PHP thread](http://www.reddit.com/r/PHP/comments/h88bl/php_shortcuts_secrets_you_cant_live_without/)

    <?php
    
        //*
        this_is_code();
        /**/
        
        /*
        this_is_commented_code();
        /**/
        
Nice quick toggle to comment or uncomment large blocks of code with one forward slash. Again
commenting/uncommenting usually means I've been debugging for a while,
but when those situations do arise they
are frustrating enough without having to scroll around to place/remove the same comment
markers over again.

Here's to a daily brain dump.
