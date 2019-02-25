---
title: Building a Movie Application with TMDB (The Movie Database) (Part One)
categories:
  - Articles
tags:
  - Development
date: 2019-02-25 15:18:38
---

So I'm on Twitter and there's this petition to [digitally remove the rat from the end of 'The Departed'](https://www.nydailynews.com/new-york/ny-news-digitally-remove-rat-from-the-departed-kickstarter-20190219-story.html). Having not seen the Martin Scorsese masterpiece in well over a few years, I decide to hop on Netflix and give it another whirl. 

What a thrill ride.

Luckily, I'm notorious for not remembering the end of films so the experience was practically fresh. With adrenaline still pumping through my veins I felt the overwhelming inspiration to give another go at my movie tracking app idea. Sure, the idea is has been implemented countless times since initially having thought it up in 2010 but the need is still there and for some reason I've been reluctant to give other solutions a go. 

So what are we building? Let's walk through a scenario: I just finished watching The Departed and loved it. I want to add it to my list of public recommendations for future reference. 

I'm less interested in the movies that aren't worth my time, so having The Departed on my list should itself have some merit. People love Top 10 lists and it would be interesting to see what my Top 10 movies are. Could be a conversation starter to compare lists and see how we compare. 

To do so, we'll need a social element of recommending movies to each other. If I'm on the app and want someone else to use it with me, I could invite them to add movies to their list. So your friend logs on and is welcomed by a list of movies and you can either add them to your list or pass. 

Tinder for movies? Imagine a couple sitting down to watch Netflix: the app presents a list of movies and you either swipe right or left, once there is a match that you're interested, you can agree to watch the movie! So, we need a list of movies we're interested in. You know you want to watch something but you don't know what.... 

Cool, we're seeing some potential. If movies are over 100 years old, movie apps might last just as long! Let's get cracking. 

To start, we'll need to familiarize ourselves with TMDB [The Movie Database](https://developers.themoviedb.org/3/getting-started/introduction). Let's start with ~~a new Codepen~~ the command line to see if we can get the basics down. 

We'll need an API key and we'll need to make basic requests. Looks like I [already had an account](https://www.themoviedb.org/u/bcommandeur). So now I can head to settings > API and grab my API key. Now I should be able to use this in Codepen to start experimenting... wait. Security. Feels bad to store my API key in public since a nefarious user could take this and make requests on my behalf, exceeding my usage limits. I googled 'vue api secret' and discovered [this tip from reddit:](https://www.reddit.com/r/vuejs/comments/78np9q/where_to_put_api_key_vuejs_app/)

```
https://www.npmjs.com/package/dotenv
import it to vue
block it in .gitignore
```

Turns out [npmjs.com/package/dotenv](https://www.npmjs.com/package/dotenv) is based on [The Twelve Factor App](https://12factor.net/), a methodology for writing web apps in any programming language. Let's remember I'm building a portfolio piece and want to build best practices from the start. While we're on a huge tangent now, I'd like to review this methodology before tackling my new app. But before we do that, let's at least get a response in the console with my new API key.

Where to begin? We know `curl` exists, so let's use that to get a response and see what happens. We already have `homebrew` installed on this machine so...

```
brew install curl
```

which causes `homebrew` to update (this takes a while) before installing `curl`. We take a look at the [curl documentation](https://ss64.com/osx/curl.html) and give it a whirl:

```
curl https://api.themoviedb.org/3/movie/550?api_key=secretapikey123
```

which returns

```
{"adult":false,"backdrop_path":"/52AfXWuXCHn3UjD17rBruA9f5qb.jpg","belongs_to_collection":null,"budget":63000000,"genres":[{"id":18,"name":"Drama"}],"homepage":"http://www.foxmovies.com/movies/fight-club","id":550,"imdb_id":"tt0137523","original_language":"en","original_title":"Fight Club","overview":"A ticking-time-bomb insomniac and a slippery soap salesman channel primal male aggression into a shocking new form of therapy. Their concept catches on, with underground \"fight clubs\" forming in every town, until an eccentric gets in the way and ignites an out-of-control spiral toward oblivion.","popularity":35.399,"poster_path":"/adw6Lq9FiC9zjYEpOqfq03ituwp.jpg","production_companies":[{"id":508,"logo_path":"/7PzJdsLGlR7oW4J0J5Xcd0pHGRg.png","name":"Regency Enterprises","origin_country":"US"},{"id":711,"logo_path":"/tEiIH5QesdheJmDAqQwvtN60727.png","name":"Fox 2000 Pictures","origin_country":"US"},{"id":20555,"logo_path":null,"name":"Taurus Film","origin_country":""},{"id":54051,"logo_path":null,"name":"Atman Entertainment","origin_country":""},{"id":54052,"logo_path":null,"name":"Knickerbocker Films","origin_country":"US"},{"id":25,"logo_path":"/qZCc1lty5FzX30aOCVRBLzaVmcp.png","name":"20th Century Fox","origin_country":"US"},{"id":4700,"logo_path":"/A32wmjrs9Psf4zw0uaixF0GXfxq.png","name":"The Linson Company","origin_country":""}],"production_countries":[{"iso_3166_1":"DE","name":"Germany"},{"iso_3166_1":"US","name":"United States of America"}],"release_date":"1999-10-15","revenue":100853753,"runtime":139,"spoken_languages":[{"iso_639_1":"en","name":"English"}],"status":"Released","tagline":"Mischief. Mayhem. Soap.","title":"Fight Club","video":false,"vote_average":8.4,"vote_count":15376}
```

Which is a JSON object for the 'Fight Club' entry on TMDB! 

Well done. Now let's post this and take a break. I'll have to navigate over to my /hexo-blog folder, and run `hexo new post`. This didn't work so I `rm -rf node_modules/ && npm install` courtesy of this [issue on github](https://github.com/hexojs/hexo/issues/2076) to resolve the `ERROR Local hexo not found in ~/...` error. 

We'll post this to github with `git status`, `git add .`, `git commit -m`, and `git push`. I already had my blog repo clone from github.