---
title: Building a Note-Taking Application for the Command Line
categories:
  - Session
tags:
  - Development
  - Web Development
  - Javascript
  - npm
  - Node
date: 2019-04-17 00:30:30
---

## What We're Building

Previously I've worked on a terminal application called **Catch**. It was built with Javascript (Node specifically) and designed to eventually be hosted on npm. The idea is to have a **git**-like history (or log) of notes (or thoughts). These notes could be recommendations, todo items, blocking points, documentation, you get the idea. Tonight, we'll be picking up where we left off.

## Plan of Action

First step is to ensure that Catch is indeed backed up and able to be worked on. We'll check out GitHub and clone the repo into my Projects folder under my Development directory. 

Second, we'll need to run the program a few times. I'd like to make the assertion that `.txt` is a better file format for Catch notes. The idea is to use these as almost sticky notes. Appending catch lets you batch delete these files or consolidate them. Instead of building a Swiss Army knife, let's build with the Unix tradition of building a screwdriver first. 

## Change of Course 

We understand the basic idea of Catch based on the prototype I built. Taking into account some lessons learned from CMPUT 302 – Introduction to Human Computer Interaction, I'm going to build (what will ideally become) a production prototype and release as version **0.1.0**. We begin at 0.0.1, and installable module from `npm` that prints "Hello World" to the screen. 

### How to Register a Package to npm (Node Package Manager)
1. We'll start with the [npm documentation](https://docs.npmjs.com/). 
2. After reading their introduction, we [create an account on npm](https://www.npmjs.com/signup).
3. We (create a scoped public package)[https://docs.npmjs.com/creating-and-publishing-scoped-public-packages].
4. We create a a `README.md` file and describe the intent of our application and document the API (Application Programming Interface).
5. We'll ensure the "name" field of our `package.json` includes `@username/package-name` so that when we publish the package it will be scoped to our username. 
6. We run `npm publish --access public` and make sure there are no errors. 
7. We create a test directory and run `npm install @username/package-name`. We should now find our package installed in the `node_modules` folder of our test directory. 

### Following a Guide on Medium

I found the following article on Medium: [Build and Publish Your First Command Line Application with Node.js and npm](https://medium.com/@cruzw/build-and-publish-your-first-command-line-application-with-npm-6192f4044779). It walks through the steps of creating a command line application (which we're doing) instead of a module that is designed to be imported into other programs.

I add the following fields to my `package.json` file as per the above article:

```
“main”: “bin/app.js”, 
“preferGlobal”: true,
“bin”: { “app”: “bin/app.js” },
```

Now we can copy/paste our code from the prototype I built into our newly created `app.js` file. I run the following command to give permission to let me run this file locally:

```
chmod u+x ./bin/app.js 
```

After implementing code changes and making sure everything works as expected, we update the version number in our `package.json` and run `npm publish`. 

Now we can run:

```
npm install -g @bcmdr/catch
```

And use the app! Future changes can be published to npm, allowing users to update by calling the above line again. 

## Finished Product

The source code for the above project [can be found in its GitHub repository](https://github.com/bcmdr/catch-cli). The published package [can be found on npm]