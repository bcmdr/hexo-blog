---
title: My Favourite Piece of Code
categories:
  - Articles
tags:
  - Development
date: 2019-05-09 09:43:18
---

There's a piece of code I posted on instagram, and it looks like this:

```js
// Universe

const properties = {
  energy: (mass, distance, time) => {
    return mass * (distance / time) * (distance / time)
  },
  mass: (energy, distance, time) => {
    return energy / (distance / time) * (distance / time)
  }
}
```

and for reasons just within my grasp, it is my favourite piece of code. 

Looking at it, I feel relaxed. Writing it, I feel productive. Learning it brings me this deeper understanding of life. Why? Because `e=mc^2` is my favourite formula. 

It is my *mystery of life*... Some kids dream of counting beyond one million. I dreamt of memorizing "e equals em see squared", which eventually became "energy equals mass times the speed of light squared (in a vacuum)". 

Now that I know **math** and **code** (and can type *very* fast), I can just write `e=mc^2` , and all that knowledge comes pouring into my brain. 

The above piece of code was designed to illustrate the beauty of objects within functional programming. I love Javascript for its choice to have functions be 'first class citizens' (they are objects, themselves). 

Its concise, and packs a punch. And can even unlock the secrets of space and time. Actually, it can't; but, maybe Einstein would have thought it was cool.
