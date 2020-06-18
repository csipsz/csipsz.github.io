---
layout: post
title:      "CLI with Mass Assignment "
date:       2020-06-18 09:49:56 -0400
permalink:  cli_with_mass_assignment
---



The CLI project that I made is based on the Ghibli API. It is listing characters and locations from the movies and you can search for additional information, like the director, producer or the summary of the stories. 

I was very scared the day before project week and I pictured myself coding Saturday all night long, but when I showed the project to my cohort lead on Wednesday morning asking him what am I missing, he said it's done. And I was thinking, really? Where did all of the work go then? 

My first concern was just creating the project. I tend to get lost in file structures and I am deeply disturbed by every extension that I don't know. Like what does .travis.yml do in my cli_project folder? Who is travis, and when did I ask for him? I guess it would be time to google it...  
But after watching my cohort lead's and Avi's videos, soon I was adding executable permissions in my terminal with the `chmod +x run` command to my executable file that I previously created and just named it run. I renamed my environment file to environment.rb... I was making sure. After an hour of following along I had a reasonable project that was showing up on my Github page and I think I made around 5 commits in my first half an hour with not a whole lot of content other than my enthusiasm over the fact that it is working. 

The most difficult concept that I faced in programming so far is object relationships so I was worried that how will I build up my program with good object orientation patterns. So after watching even more Data Gem Walkthroughs I decided to start with my CLI class and just put in mock data first to implement the project flow. I feel pretty strongly about if statements and usually recursion, calling methods inside other methods is pretty clear for me. When I miss my scope it is not that hard to debug. So this part was done pretty easily but it felt like playing instead of hard work. Like when you write your first "Hello World" puts, print, or console.log() sentence and codecademy or learn.co congratulates you on writing your first program. 

Finding an API that is free, doesn't need an API key and doesn't have a limitation on API calls was very difficult so I really need to improve my efficiency in internet research. I ended up with an API that I like but it is very small so my project turned out a bit uneventful. But I thought I had no time to waste and I wanted to focus on object orientation and fetching the data. 

My API class ended up with three methods collecting data from 3 different endpoints using RestClient and parsing with JSON. 

And my three classes had their initialize method, their attribute accessors, their class method to return all of the instances, and they were implemented with mass assignment. 
```
class Character 
attr_accessor :name, :age, :films, :gender, :species, :eye_color, :hair_color, :id, :url

@@all = []

def initialize(attributesHash)
attributesHash.each {|key, value| self.send(("#{key}="), value)}
@@all << self

end
```

I heard that being lazy is a merit in coding, but I was wondering if there is such a thing as too DRY. I am guessing that in my case there might be, because I was getting information that I never intended to use. I knew that I don't want the id or url, but mass assignment seemed so easy and elegant and I just wanted to try it out. If I can collect more information with less line of code from a very small API, so getting too much data is not going to matter, I figured I'd just do it. 

So Tuesday night I was puzzled thinking okay, the CLI.rb was the fun part, my API class only has three methods, all of my classes barely have anything else than initialize in them... I could create a method that was converting the url value into the actual title that belonged to a certain character or location, and I thought that this is where all of my creativity went. So I was wondering, what am I missing, where are all of my class methods? My program works, it lists characters or locations, you can pick, and you can also look up the movie that belongs to the character. But working code doesn't always mean that it is good. 

So I was very surprised when I heard that it is good to go, and I guess I will learn more about it during my project review!
Until then I am happy to take a quick break because I think I made it sound very easy, but in reality I am very exhausted from sitting in front of my broken code for many many hours. 









