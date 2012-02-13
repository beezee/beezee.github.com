---
layout: page
title: Brian Zeligson | Random thoughts on web development
---
{% include JB/setup %}

{% for post in site.posts %}
  <div class="post">
  <h3><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h3>
  {{ post.content | strip_html | truncatewords: 25 }} 
  <p> <a href="{{ post.url }}/#more" class="more-link"><span class="readmore">Read the rest of this entry »</span></a></p>
  </div>
{% endfor %}



