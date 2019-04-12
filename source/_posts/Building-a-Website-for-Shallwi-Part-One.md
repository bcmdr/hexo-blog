---
title: Building a Website for Shallwi (Part One)
categories:
  - Sessions
tags:
  - Shallwi
  - Development
  - HTML
  - Parcel
date: 2019-04-12 03:47:28
---

So we're in the process of developing a new landing page for Shallwi. A few decisions have already been made along my tinkering process and I wanted to capture them. This will hopefully: (1) slow my pace, ensuring I'm thinking my solutions through; and (2) chronicle these decisions so I can reference back to them later. 

Here's what we have so far.

## Choosing a Tech Stack 

I landed on trying to build the site "from scratch". I want to harness the speed and flexibility of pure HTML, CSS, and JS while also having access to modern "nice-to-haves" like hot-reloading. Without the guidance of a framework like Gatsby or Vue-press, I'll be forced to consider each aspect of the website myself (SEO, optimization, etc) without assuming it's magically being done for me (which might not be happening anyway). 

I'm aware of Parcel as a lightweight bundler that some developers prefer over Webpack. Having worked with Webpack before I'd much prefer the simplicity promised by Parcel than having to tinker with that stuff myself again. I assume I'm going to be bundling files in some way if I want a well-organized file structure so we'll use that as our "core technology" for now and see how it goes. 

## Creating a Github Repo

Choosing a "core technology" fits into my naming structure for git repos. I've found it beneficial to name by 'context-project-technology' to help me find the projects later. The *context* here is 'shallwi', the *project* is 'site' (as opposed to 'app' or other type of deliverable), and the *technology* is 'parcel'. 

We have to name our repo something to start and this naming technique lays out the intent of the repo as well as versions it by what technological decision will behave as the foundation for later decisions. It's not too verbose, either which makes it nice to work with. 

## Choosing a License and .gitignore

These might be trivial in the long run but I'd like to lay out my rationale of considering this early on. We could add these later but, again, I'd like to be able to document my intent by the choices themselves. I can change my mind later on (by adding to the `.gitIgnore` file or changing the license), but here I'm flexing my decision making muscles but treating nothing as trivial and giving it its due thought. 

Ultimately I chose a *node* based `.gitignore` file and *The Unlicense*. I'll be using npm or yarn at some point with Parcel so the node choice makes sense (I added some macOS specific stuff since I'm developing on mac). I'm also a fan of open source and The Unlicense feels like a good place to start. 

## Choosing a Boilerplate

I've decided that in lieu of something like HTML5 Boilerplate, I'll be following the [MDN Documentation for HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/Introduction_to_HTML5). The Mozilla docs are the most trust-worthy in my opinion and this will make sure I take nothing for granted during the development process (again, being mindful with each decision). 

Actually, it turns out the above HTML5 reference page on MDN links to [the HTML5 spec itself](https://html.spec.whatwg.org/) so I'll be using that (it goes through each element specifically which is what I'm looking for).

## Getting Started with Parcel

Now it's time to clone the starter repo and initialize Parcel. Following the [Parcel getting started docs](https://parceljs.org/getting_started.html) gets me to set up an initial HTML file, to which I add a *DOCTYPE* to as per the [HTML5 spec requirement](https://html.spec.whatwg.org/#syntax-doctype), with a bundled JS file.

Running `parcel index.html` gives me the hot-reload server I'm looking for (glad to see it works).  

I'd like to commit some initial files before ending for the night. First, I replicate the content of the [mockup I made in Figma](https://www.figma.com/proto/gpxMPIkbZx77em25WXvrVyht/Shallwi-Site-Design-%E2%80%93-Comic-Relief?node-id=1%3A93&scaling=scale-down) with semantic HTML. Working with this already yields a file that's nice to read and reaffirms my decision to not start with a framework. Next, I add `.cache/` and `dist/` to my `.gitignore` upon seeing them with `git status`. 

I push this code to GitHub and call it a night, but not before updating my `README` file with the resources listed in this blog post and publishing this session. 