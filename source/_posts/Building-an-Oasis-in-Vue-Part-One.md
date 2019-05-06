---
title: Building an Oasis in Vue (Part One)
categories:
  - Sessions
tags:
  - Development
  - Vue
  - Oasis
date: 2019-05-06 02:34:00
---

## What is an Oasis? 

It's a place in which a programmer can relax, try things out and escape into their own little world of code. It's more than a portfolio: its the place in which your portfolio is created. 

My Oasis is my writing app (IA Writer), my terminal (Hyper.js), my code editor (VS Code) and my browser (Firefox).  A lot can happen in these few apps, and adding a layer of my chosen frontend framework can further its capabilities. I'm choosing Vue. I'm excited to go back to that "all in" dedication that drove me to learn it in the first place. My goal here is to create a CodePen style system in which I can prototype my designs (created in Figma). 

## I'm choosing Vue 

because their .vue files have been the most enjoyable to work in and still makes the most sense from the many 'css-in-js' solutions out there. They're simple, clean, and easy to work with, and they already share the CodePen structure of Markup/Style/Behaviour (HTML/CSS/JS). Much like my blog is a collection of mark-down files, I'd like my oasis to be a collection of .vue files. Let's start there. 

## Project Creation Experimentation

We'll create a GitHub repository with the project name and the intended "main" technology: (https://github.com/bcmdr/oasis-vue)[https://github.com/bcmdr/oasis-vue]. ~~After importing this locally, we'll initialize my npm project with vue.~~

```
git clone https://github.com/bcmdr/oasis-vue.git
npm init -y
npm install vue
```

~~I notice Vue has a parcel installation step so I'll shortcut this selection and opt in to using parcel as my default bundler alongside Vue as my default framework.~~ Vue has a built in bundler with Vue-cli I can use for prototyping. 

```
npm install -g @vue/cli-service-global
```

Instead of installing vue locally, let's use the global cli to create a base vue application. 

``` 
npm install -g @vue/cli
vue create test
```

This creates a completely self-contained app, so we'll delete the created repo and upload this instead.

So finally, we have the creation steps as follows:

```
vue create oasis-vue
cd oasis-vue
git remote add origin https://github.com/bcmdr/oasis-vue.git
git push -u origin master
```

## Making it Work, Pushing it Live

After some initial tweaking of the default app, we have an imported component running locally on my machine. To call this session to a close, let's see if we can build the Oasis on Netlify.

After pointing to our GitHub repo within the Netlify 'new site from git' button, we set `yarn run build` as our build command and `dist` as our target directory. 

Now, with every push to Github, Netlify will import our code, use `yarn` to compile our `.vue` files into browser-readable code in this newly created `dist` folder, so that when people head to (https://bcmdr-oasis.netlify.com/)[https://bcmdr-oasis.netlify.com/], they'll end up on the 'index' page of our newly create Vue application. 

Neat! Everything is working. Let's call it a night.
