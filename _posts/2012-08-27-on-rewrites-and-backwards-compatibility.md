---
layout: post
title: "On rewrites and backwards compatibility"
category: General Development
tags: ['Best practices']
---
{% include JB/setup %}

Today I am wrapping up a major rewrite for Streetwise Media, using our new
[MVC framework](http://streetwise-media.github.com/Streetwise-Wordpress-MVC/).

I found myself making tweaks to the current codebase to support rollback if necessary, when I started feeling something was
wrong. Backwards compatibility should always be implemented in a new codebase, not the old. Where I encountered this today,
and where I expect the common choke point for compatibility in a full rewrite resides, is in the data persistence.

If you were storing something one way, keep storing it that way. If you have a legitimate reason for restructuring your
persisted data, maybe that should be done seperately from a major rewrite.

Instead of this in the old code:

    <?php
    
        $data = get_data();
        $data = json_decode(json_encode($data), true);
        
Just do this in the new code:

    <?php
    
        $data = json_decode(json_encode($data), true);
        persist_data($data);
        
By the way, here's an easy way to convert an object instance to an associative array:

    <?php
    
        $array = json_decode(json_encode($object), true);
