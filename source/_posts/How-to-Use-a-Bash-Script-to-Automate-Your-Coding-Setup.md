---
title: How to Use a Bash Script to Automate Your Coding Setup
categories:
  - Tutorials
tags:
  - Development
  - Terminal
  - Productivity
date: 2019-05-06 23:02:19
---

## The Problem

Every time we sit down to code, we find ourselves starting with the same commands:

```
cd ~/Development/Projects/hexo-blog
git pull
code .
```

What I'd like to do is type `./dev` and automatically run the above commands at once. 

## Enter Bash

To do this, we're going to create an executable script file that can run in our terminal. The most common approach
is to write a script (series of commands) meant to be executed on a particular terminal language. The commands we intend to use are meant for the bash terminal, so we'll create the following file:

```
#!/bin/bash

cd ~/Development/Projects/hexo-blog
git pull
code .
```

And save this file as `dev` (no filetype on purpose). We need to then give our computer the "ok" to run this potentially volatile series of commands as a neat little app. For this we'll run 

```
chmod +x ./dev
```

which will "change mode" such that "executable" is added to the file "dev" in our current diretory ("./").

Then we can run `./dev` as a single command in whatever directory that dev script is saved in. For example, my dev will navigate to my blog's project folder, pull any new changes, and open the directory in VSCode. 

