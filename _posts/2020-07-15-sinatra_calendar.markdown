---
layout: post
title:      "Sinatra Calendar "
date:       2020-07-15 18:08:57 -0400
permalink:  sinatra_calendar
---


I chose a fairly simple idea for my Sinatra project because I wanted to have strong foundations for the upcoming Rails module. Everyone says that Sinatra helps to understand Rails better, and everyone also says that Rails is magic. So I was reading through very long ActiveRecord documentations before the project week, trying to familiarize myself with the CRUD actions provided by ActiveRecord as well as Migrations and Rake tasks. I thought that the project itself will be much more difficult because in the beginning I had a lot of syntax error in my erb files. But in the end building my project was a lot of fun! 

My app only has two models, a User and an Event model. It comes with four controllers, a sessions, a users and an events controller, which all inherit from the application controller. I was trying to follow the RESTful routes conventions as much as possible, but there are still some grey areas for me. I put my "/signup" route into my sessions controller, since signing up provides the session hash with a new user_id key and it seemed pretty logical if you look at the functionality. But I can see how it is completely sensible in the users controller as well, since signing up creates a new user, so it should be in the "users/new" route. I guess programming in general is its own language as well. I hope that by coding more and seeing others it will be more obvious for me as well that how to talk code. 

I am not too big on styling so Materialize was perfect for me. It is a front-end framework that makes designing with CSS very easy and fast. I spent around a day with styling which is a lot if you look at my end result. Still, when I started to build my project with the Corneal gem I thought that this light blue and Sinatra's face is very comfy, maybe I should just keep this, I won't be able to do better than that. But in the end, I think I did. 

My web application is a hybrid between a calendar and a social media site. It doesn't have a slot for every day, but it lists the events in a calendar-like grid and orders the events by date. You can look at all of the events in the home page or you can list your own events. You can do the basic CRUD actions on every event that belongs to you and I built out a mentions functionality. You can look up the events in which you are mentioned and you can look at all of the other user's mentions. It will also let you know that who was talking about you in their event. I provided my users with the possibility of deleting their account which removes all of their events from the main wall and they will be erased from the users list. I made my website pink which is quite unprofessional but I wanted to make something that I like while I am still at school and I am free to do so. 

In this project I really enjoyed the private and helper methods that make my code more dry. My views are full of inline CSS and I am not super pleased with that, but I think that my controllers are dry enough. I came up with a very simple helper method that helped me manage my urls and make sure that for example someone can't just jump to the events/new page and create a new event while no one is logged in. I didn't want to see nil as the value of the user_id in my database. 
Here is my helper method:

```
def redirect_root
      while !logged_in? 
        redirect to '/login'
      end 
    end 
```

It is super simple, but it saved me 5 or more if else statements. I know that the root is the welcome page, but my method name helped me focus on what I wanted to do. Altogether I really enjoyed the Sinatra project and I am very excited to learn about Rails. 
