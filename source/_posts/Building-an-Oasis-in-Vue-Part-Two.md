---
title: Building an Oasis in Vue (Part Two)
categories:
  - Sessions
tags:
  - Development
  - Vue 
  - WebDevelopment
  - Parcel
date: 2019-05-07 22:08:59
---

## The Problem With a Default Framework

I may have worked myself into a corner here. I'm looking to create a local / offline / custom CodePen type system that would let me prototype and then display these unfinished products as a gallery of components / pages. 

I'm realizing that some of my projects may not be best suited by Vue, as I may instead want a traditional html/css/js file setup. Limiting myself to Vue components may not be as future-proof as I'd like my portfolio to be. 

## A Change in Direction

So instead I'm thinking of using Parcel. With Parcel I'll have a collection of files that can be bundled together and built into a static site. The first problem I think of is how difficult / tedious the boilerplate will be when I'm adding new pens / pages / projects. 

We gotta think old-school web here. Index page with a directory to the different projects. That is timeless.

## Back to Basics

So we can take what we've learned from trying to build the Shallwi website from scratch and instead create an environment that is easy to drop web page bundles into. I'm coining the phrase 'bundles' on the fly to refer to the following structure:

```
bundle-name/
- index.html
- index.css
- index.js
```

In theory a bundle could be the `dist` folder of a production-ready Vue project. I'm thinking, though, about web page bundles as components themselves, building blocks for larger web pages, a means of composition of sites (a collection of pages). 

It will take some experimentation, but ideally I'll come up with a (or find an existing) way to compose a website through drag and drop, essentially. Hmm... Yes. Drag and drop in the sense that we can string a Vue project with a react project with a html/css/js (HCJ) project. 

Problem: we wanted this to be an opinionated "oasis" in which to work on designs. Solution: the term oasis was chosen to induce a feeling of freedom, this is a feature, not a bug. 

Alright, so bit of a misnomer in the title so let's try again:

## Building an Oasis with Parcel (Part One)

So what do we want by the end of this session? I should have a template file structure for a bundle. I should have two of these bundles in a project each accessible from the index of the portfolio. 

File structure brain storm:

```
portfolio-name
- /index.html
- /index.css
- /index.js
- project-name-1
	> /index.html
	> /index.css
	> /index.js
- project-name-2
- project-name-3
```

So let's begin with a parcel-oasis project on GitHub, initialized with Parcel. Why parcel? We're going to want access to new javascript syntax since this is an experimentation portfolio. Parcel makes this stuff work "automagically" and should give me flexibility in the future. It's a batteries included Webpack competitor and it's way quicker to setup. 

I'll start in the command line to see what parcel does out of the box, in case it has a CLI. [The getting started documentation](https://parceljs.org/getting_started.html) has us setup an npm project from scratch, so let's start on Github to initialize with some sane defaults. 

## Quick Sidebar

I want to note that this is an opinionated choice. Parcel implies we will be linking directly to `/index.html` which is not "pretty". We are making a statement that says, yes: this is raw html at its core to both encourage and remind that we are trying to get "back to basics" in our overall approach to web development". You could make an oasis in Vue, but I'm instead making it in Parcel. Maybe I'll make a Vue one later on. Either way, this should better illustrate my intent of declaring parcel from the get-go. 

## Back to Setup

I've noticed I have a nice starter folder structure for parcel that I'd like to save as its own repo in my GitHub. Let's make sure we have the basic portfolio structure illustrated in our defaults as outlined above. We'll reference the (parcel-shallwi-site)[https://github.com/bcmdr/shallwi-site-parcel]. I found a bunch of resources I included in the readme for that project which I'll include in my parcel-starter.

Most sensible way to go forward is to save the progress I've made on parcel-starter in place at parcel-oasis. I should then fork parcel-oasis at this point. I've had difficulties with forks before, so I'm tempted to copy paste, but I'd rather deal with learning why I had those older issues. Right, the issue was that I need to fork it into an organization on Github and then I have to worry about not having it sync (the fork's default behaviour). For simplicity I will copy and paste into a fresh repo. 

We manually created the repo with some fine tweaking and now have (parcel-starter on Github)[https://github.com/bcmdr/parcel-starter]. Which I can hopefully reference later and add more starter resources if this oasis idea takes off.

## Wrapping Up

Lots of progress made tonight and am liking the direction of a parcel-centric system. Next steps would be creating my parcel-oasis from parcel-starter to see if I can get that going as a jumping off point (and potentially be the workflow to teach to future hobbyist developers as my technique). We're getting better at "making it a thing" as Scott Tolinsky says, turning each bit of development knowledge into a reference able project for myself and others. I'm itching to keep tinkering but for the sake of this post, let's call it a night. 