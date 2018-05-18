---
title: How to Upload a Starter Files Repository to Your Personal Github
date: 2018-05-16 21:14:34
categories:
- Tutorials
tags:
- GitHub
- Web Development
- Development
---

## Short and Sweet

```bash
$ git clone <someone-elses-repo-url>
$ git remote remove origin
$ git remote add origin <your-new-repo-url>
$ git push -u origin master
```

## Step 1: Download the Starter Files

Let's say you forgot to fork the repo on GitHub and have downloaded a starter files repo via `git clone`. You could go back and start over with a fork but we're here now so let's move forward. 

## Step 2: Change Your Remote Settings in Git

Github will tell you to `git remote add origin <your-repo-url>`. So you'll do this and try to `git push` only to realize you're still trying to push to the original owner's repo. What's needed here is a `git remote remove origin` followed by `git remote add origin <repo-name>`. That first part will start you off fresh. 

## Step 3: Upload to Github

Now you can `git push`. Github will ask for your login credentials and you'll now have the starter files safe and available on GitHub. 
