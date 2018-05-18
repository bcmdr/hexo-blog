---
title: Building a Website from Scratch
date: 2018-04-21 13:58:23
categories:
- Articles
tags:
- Web Development
- Development
---

## What we have used so far:

Hyper as my command terminal to create the website directory
- `mkdir ~/Documents/Website && cd ~/Documents/Website`
- Where documents is my iCloud storage home. 

An index.html page to serve as the home page for content
- `touch index.html`

A Readme.md to serve as a homepage for documentation
- `touch README.md`

VS Code as my text editor of choice
- `code .`
- It's popular and powerful, a joy to use once you get used to it. 
- [Launching VS Code from the terminal with the 'code' command](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)

Git and github as my source control and version history 
- `git init`
- Prefer netlify install of estabished git repos and proper .gitignore files.

A static site generator to convert my md blog posts into html. 
- [Jekyll](https://jekyllrb.com/) - Distractingly unfamiliar
- [Hexo](https://hexo.io/) - Uses node over ruby so I can bring over my js experience

Netlify as my webhost
- deploy to netlify button as my one step install of a server and github repo. although this didn't actually work, had to fresh install hexo as the netlify deploy deploys the official hexo website. 

Minos as my Hexo Theme
- Looks like Medium and has search built in. 
- Also uses Bulma as its framework, which I've learned how to customize. 

## Content Driven Development

Lately I've been doing a lot more writing and music creation. The goal is to be able to write music or blog posts as they come up and host them in their natural file formats. For blog posts I like working with markdown and would like a way to host these markdown files with little to no extra work when publishing. Same goes for mp3 files which naturally I'll be working with for music. Simply dragging these files into their appropriate directories in my website structure should allow for them to be hosted. This is in contrast of using content hosts directly which couple the source of the file to that specific host.

The dream is to have all my files available locally while trusting these files to be available in website format when needed. These needs involve sharing the creations or listening to them later on. I've been frustrated with navigating DropBox or IA Writer when I'm on the go so and love the simplicity of going to a url instead. I want to have a single url that makes available everything I've created worth sharing. I also want to capture the process of creating these things as something worth sharing in itself. 

It is also a tremendous learning opportunity to try and use the web as a solution to hosting content. Obviously this is what the web is for, but most of my work so far has involved tinkering for the sake of tinkering, taking for granted what many of the solutions I was playing with are actually built for. I enjoy web development but realize that all of my successful web development progress has revolved around hosting something specfic and solving a specific problem. That problem again for me currently is wanting to share the content I produce from a central hub. Coasting on the progress of others has blinded me to why they made their progress in the first place. That is, the technologies I've been learning were built for a reason, so building something "from scratch" should help me discover those reasons and better appreciate the tools I use. 

## Choosing a Static Site Generator

While I enjoy scaffolding HTML pages from scratch, the reality is that doing so becomes cumbersome and adds friction to the content producing work flow. I've used a static site generator to handle the busy work of converting markdown posts to html pages properly structured and organized for navigation in a web browser.

The initial project was to create a website from scratch, introducing complexity as needed to solve specific requirements. The first two requirements were hosting markdown files and hosting mp3s. The static site generator was instantly recognized as needed to overcome the maintence involved with blogging. While instantly more "complicated" than manual html pages, the simplicity in automation that comes with the generator justifies the learning the curve. Static site generators support static assets by default so my mp3 requirement is also met.

Hexo ended up being my static site generator of choice, mainly because it is well reviewed and built on node. My javascript knowledge makes for a simpler learning curve compared to learning ruby for using Jekyll, a more widely used SSG.  
