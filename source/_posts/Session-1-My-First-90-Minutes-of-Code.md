---
title: Session 1 - My First 90 Minutes of Code
categories:
  - Sessions
tags:
  - Development
date: 2019-03-28 16:41:50
---

[Begin 4:30PM on March 28, 2019]

Today's post comes from the inspiration of my previous post on **90 Minutes of Code**. The goal is to work on a programming challenge for upwards of 90 minutes and see how it goes. 

The format recommends 10 minutes of blogging before we hit the code. This will allow us to brainstorm priorities and ensure we end up focusing on the right challenges. 

My blog, built with Hexo and hosted on Netlify, is my current interest. I noticed that I could add a new category of post called `Session` to join `Articles` and `Tutorial`. Having this new category makes way for a daily journal that doesn't "pollute" the other categories. 

Let's get started.

First step is to download my hexo blog from GitHub and figure out how categories are made. I have 2 existing categories so I should be able to figure this out relatively quickly.

I wonder if I can add a new category and if hexo will figure it out from there.... Let's find out. I'm going to `hexo new` and see what happens if I change the category from Articles to Sessions. Oh! I can make a post in hexo for this very session. 

`hexo new post "Session 1 - My First 90 Minutes of Code"`

I'll enter that into my terminal in my `hexo_blog` repository folder and copy in the body of this post up until this point. 

I'd like to build and preview the blog locally at this point so I'll `hexo server` as per my `README.md`. This didn't work as I got a "No layout: index.html" error. I remembered that Minos, the Hexo theme I'm using, is connected to my blog as a git submodule so it needs to be imported separately. 

I found this command `git submodule update --init --recursive` and ran it from the minos theme directory within my hexo blogs's themes directory and it installed. 

I ran `hexo server` again and it worked! Well some of it worked. I can see my blog post with the category of `Sessions` but no `Sessions` link in the nav bar. I probably have to configure the hexo config file so I'll find that in `_config.yml`. But! I have to update the config of the minos theme, not hexo itself. 

There's a `menu` object in the Minos theme config to which I can add `Tutorials: /categories/Tutorials`. This worked! I can now see *Sessions* in the nav bar.

Now for a point of reflection. I've been working now for 30 minutes and I've accomplished one of my goals. I notice that I'm enjoying blogging along side the programming because it helps me organize my thoughts and I can reference back to this later if I forget what I did. I'm also hoping there is some SEO relating to my error message and theme name. This format is pretty verbose and may be difficult to parse, but it's better than nothing and ultimately aids in my learning (plus it's fun!)

Let's post the change to the github after a quick test, allow Netlify to work its magic of updating my blog, check the live changes and take a 5 minute break.

I ran into some issues with pushing the changes of my submodule (the minos theme) but what worked is 

```
git branch add_sessions_category
git checkout master
git merge add_sessions_category
``` 

where `add_sessions_category` is an arbitrary name of the temporary branch from which to merge.

