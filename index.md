---
layout: page
title: One Infinite Loop
tagline: Sophia Feng Blog
---

Welcome to my site! Nice to meet you here. I just started blogging on GitHub this week. Rooms are there, waiting to be decorated. If I'm not greeting at the the doorstep, I must be doing some paintwork upstairs. Hi there!

### Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

### More posts incoming.
