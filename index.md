---
layout: page
title: One Infinite Loop
tagline: Sophia Feng Blog
---

![] (Fig/InfiniteLoop.png) 

Welcome to my site! Nice to meet you here. I just started blogging on GitHub. It's so much fun. I used to take notes on Evernote recording procedures for later references and writing digests to summarize thoughts. Blogging is another way of note-taking, only focused on technical topics. I blog to encourage myself learn. It also makes the infinite loop more enjoyable. 

## One Infinite Loop
"Weariness that wants to reach the ultimate with one leap, with a 
death-leap; a poor ignorant weariness, unwilling even to will any longer:
that created all gods and afterworlds." - Thus spoke Zarathustra.

I like this quote of Nietzsche. But don't take the ancient prophet's words literally. One death-leap that can end all cases will be a modern man's daydreaming. We're practically death-leaping after death-leaping driven by deadlines after deadlines. No rest for the wicked, and not much for the virtue.

However, we are not condemned to ceaselessly roll a rock and laboring in vain. We get somewhere. We've improved ourselves through every new task:

- new skills acquired√.
- new knowledge absorbed√.
- new experience accomplished√.

which leaves us in a far better place than Sisyphus. Lucky enough, we live in the best era ever: NOW. With millions of opensources we are free to learn almost whatever we want. Education is still luxury but there are alternatives. I sing praise for our time. And verily, verily I applaud this infinite loop

    while alive:
        learn
        produce


Learn, produce and improve, I cannot think of a life happier than this. 

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## More posts incoming.
