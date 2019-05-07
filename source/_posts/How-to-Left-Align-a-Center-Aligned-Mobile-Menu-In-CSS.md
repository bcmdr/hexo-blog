---
title: How to Left-Align a Center-Aligned Mobile Menu in CSS
categories:
  - Tutorials
tags:
  - Development
  - CSS
  - HTML
date: 2019-05-06 23:18:14
---

## First Attempt

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

I much prefer the readability of left-aligned word wrap. It also scales more consistently for larger screens.

## Second Attempt

Implementing the above code worked well at first glace, but later testing revealed the above code create weird spacing issues where now my menu items were no longer vertically aligned. It turns out the Minos Theme is using flex-box, so
declaring `display: inline-block` broke the spacing that flex-box provides. So instead:

```
.navbar-item {
  text-align: center;
}

```

becomes

```
.navbar-menu {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
}

.navbar-item {
    text-align: left;
}
```

Now we have vertically aligned menu items that wrap to the next line on narrower screens.