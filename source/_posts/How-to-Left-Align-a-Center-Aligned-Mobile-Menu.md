---
title: How to Left-Align a Center-Aligned Mobile Menu
categories:
  - Tutorials
tags:
  - Development
  - CSS
  - HTML
date: 2019-05-06 23:18:14
---

So we've noticed that our menu has center-aligned items. We instead wish to left align these items and have them wrap in a more readable way. Turns out it's two lines of CSS:

```
.navbar-item {
  text-align: center;
}

```

becomes

```
.navbar-item {
  display: inline-block;
  text-align: left;
}
```

I much prefer the readability of left-aligned word wrap. It also scales more consistently for larger screens. Better alignment means less cognitive strain and better ease of use. Details.