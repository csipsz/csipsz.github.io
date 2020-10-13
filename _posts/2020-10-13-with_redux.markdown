---
layout: post
title:      "with Redux "
date:       2020-10-13 15:17:19 -0400
permalink:  with_redux
---


I know that hooks are becoming mainstream and Redux is less popular nowadays, but I am really happy that I had the chance to work with the latter. Redux felt so complex at first but gradually it made so much more sense. It gave me the confidence that only because I don't understand everything for the first time doesn't mean that I will never understand it or be able to use it. In the end I loved working with the REDUX_DEVTOOLS_EXTENSION and see all my dispatched actions and state in the browser's console. I think that my application didn't really require Redux due to it's simplicity and I am definitely planning on building React apps with hooks in the future yet I still feel like that learning Redux was a great coding exercise.

One of the other challenging part in this project was to design the whole application in an expandable and logical way. I am sure that I will need to refactor some, but this is where the beauty of React really shines: moving around components is so easy it almost feels like playing a video game. I could move around and insert components almost effortlessly and I am sure that this feature of React will come in handy later as well.

My most interesting bug in this project was that dispatching my delete action deleted my tasks and worked in the back end, and yet it throwed me a syntax error: **Unhandled Rejection (SyntaxError): Unexpected end of JSON input**.  To get out from the error page, I had to refresh, so it was fetching my data again, and in the new fetch request it didn't show the deleted task anymore. I was looking at my URL  ``http://localhost:3001/tasks/${task.id}`` and at the configuration object that came after it, because that is where the error pointed, and had no idea what is wrong. I was looking for a syntax error, maybe a missing comma. And the solution was that in the Rails back end in my destroy action it only had `@task.destroy`, and missed the `render json: @task` line. I used `rails g scaffold` and only touched my back end when I added an extra column to my database table and whitelisted the parameter in the strong params. So lesson learned, next time if I use Rails magic I will  look more closely at the code that it generates for me... 

Right now I am before submitting my last project yet  I am already thinking about the time I will have once I graduate to modify not just this project, but expand the previous ones as well, and even more excitingly, build new ones! 

If I think back to the last half a year I am so amazed by the fact that at every single project I thought that the previous one was so easy, but this one is challenging! I think this means that the curriculum was built up very wisely and I also practiced and learnt a lot. Object Orientation in the CLI, ActiveRecord in Sinatra, Omniauth in Rails, connecting the front and the back and in Javascript, and Redux in the final project... These were all things that I found difficult to grasp at the time, but now they feel much more natural. I am very satisfied with everything I learned but I also think this is just the beginning, there is so much more to coding and I can't wait to be better at it!




