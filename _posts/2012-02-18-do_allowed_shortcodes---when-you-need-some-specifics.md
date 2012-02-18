---
layout: post
title: "do_allowed_shortcodes   when you need some specifics"
category: wordpress
tags: ['shortcodes', 'security']
---
{% include JB/setup %} 

We've got two levels of public facing content submission. One is for any registered user, which obviously is protected by a heavy duty captcha, and only allows the most
basic HTML. The other is for partners with special accounts, who get their own taxonomy and custom post type. These folks get access to full fledged management interface,
including author managment, taxonomy display config, and a front end post editor with support for tagging, categorization, image upload, etc. We had a request for video
shortcodes to be made available, and since what they can't do themselves, our editors have to do for them, it was an easy decision.

The problem here arose from having to open every type of shortcode to the front end interface. Obviously this would be too drastic a measure to take, particularly since some plugins
create shortcodes quietly behind the scenes, and a shortcode can trigger any code that's written into it, independent of the access level of the current user.

Our solution was the function below, which I personally feel would be a great addition to the core codebase. Feel free to voice yourself over [here](http://core.trac.wordpress.org/ticket/19806) if you think so too.

    function do_allowed_shortcodes($content, $shortcodes=array())
    {
        //if no allowed shortcodes are provided, strip all shortcodes and return content
            if (empty($shortcodes))
            {
                    return(strip_shortcodes($content));
            }
        //foreach allowed shortcode provided, build the necessary regex to temporarily change [shortcode] to {shortcode} and then back
            foreach ($shortcodes as $shortcode)
            {
                    $allowed_matches[] = '/\[('.$shortcode.'[^\]]*)\]/';
                    $restore_allowed_matches[] = '/\{('.$shortcode.'[^\}]*)\}/';
            }
        //change safe shortcodes from [shortcode] to {shortcode}
            $safe_content = preg_replace($allowed_matches, '{$1}', $content);
        //strip remaining [shortcodes]
            $clean_content = strip_shortcodes($safe_content);
        //change {shortcodes} back to [shortcodes] and return result of do_shortcode() on that content
            $trimmed_content = preg_replace($restore_allowed_matches, '[$1]', $clean_content);
            return do_shortcode($trimmed_content);
    }