---
layout: post
title: "Jekyll Bootstrap - How to Add Navigation Tab"
description: ""
category: "essay"
tags: [jekyll Bootstrap, blog]
---

I wrote an [About Me] (http://fengs.github.io/about.html) page and would like to put it onto the navigation menu atop. Previously there were four tabs
- Categories
- Tags
- Pages
- Archive

Examining the four corresponding html files in the root folder, say Categories.html, you'll find a group assignment in the meta-date
   
    ---
    layout: page
    title: Categories
    header: Posts By Category
    group: navigation
    ---

And the group variable is taken care of by /_includes/JB/pages_list during rendering. Figured this out, adding an **About Me** tab is as easy as adding one line in about.md:

    group: navigation

Now the tabs should be listed in alphabetical order after re-compiling. 

