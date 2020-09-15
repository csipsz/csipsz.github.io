---
layout: post
title:      "The Front End Philosophers"
date:       2020-09-15 13:14:40 -0400
permalink:  the_front_end_philosophers
---


I am starting to realize that being able to understand the back end of an application is really just half of the work. Before I came to Flatiron School, I used to think that back end developers do the real work and the front end developers are just playing with CSS colors and having fun styling. So I am starting to learn the hard way that this is not the case. 

Synchronizing the JavaScript classes on the front end with the Rails back end is one thing, then I had to make sure that I am not displaying the same information twice and clear my HTML elements before repopulating it with information. If that wouldn't be hard enough, I got distracted when a div overlapped another, the div disappeared but the border stayed, a CSS Selector overwrote another, and the list goes on and on... On top of that, I spent too much time with actually finding useful information snippets for my Philosophy API. So I am starting to see that the front end development needs a lot of patience, the ability to see through all the details, and it takes a lot of devotion to create a website that is not just useful but also has an appealing user interface. I was very enthusiastic to create my app and especially to make my own API, but I was also surprised that how difficult it can get, and how quickly. 

My project at this point is just my MVP version, so I am very excited to checkout a new git branch for it and breaking it while refactoring without the consequences. Right now it is only fetching the study notes about the philosophers when you need them (so, when you click the notes button) but this way it creates duplicates in my front end if I create a note first, which saves it to my Rails back end, end then I request all of those notes. I think I will also try out listening to the DOMContentLoaded event, because I just avoided the problem with the shortcut that I found in the curriculum. This defer attribute is so convenient but being able to do things in different ways is very important as well. 

```
<script src="javascripts/index.js" defer></script>
```

Another thing that was a bit challenging is following through *what is this.* I was logging it to the console or hopped into my debugger many times through building this project. Sometimes it seemed a bit unclean, but I heard that this is what I will see in React as well. 

```
static displayBranches(){
        Branch.all.forEach(branch => branch.showCard());
    }

    showCard(){
        const div = document.createElement('div')
        const h1 = document.createElement('h1')
        div.appendChild(h1)
        branchDiv().appendChild(div)
        h1.textContent = this.name 
        h1.classList.add("clickable")
        h1.addEventListener('click', this.display.bind(this))
    }
```

The last line of code of this snippet was my most concerning moment in the project, thinking *isn't there a better way?*
So basically I created a Branch class for each big philosophical topic, like Metaphysics or Epistemology, added a class method so it iterates through all of them and calls the showCard() instance method on each of them. Here I create a card, display the name in a header, add a class to it so when you hover over it you can see that if you click on them you can have more information. And then, I added the Eventlistener to the header that shows the branch name, but then *this* becames the HTML element that the event was called on. But I wanted to use my display instance method in a way so *this* inside of it is the instance of my branch, that I try to display. So calling the instance method on *this* (which is the instance of the branch in showCard()) and then bind it to *this* (to make sure that *this* stays the branch instance instead of the HTML header) seemed like cheating. But apparently it isn't, and I am very glad that I ran into this case, because it showed me the power that call, apply and bind has - I think I understood these functions a bit before, but seeing what they are good for will hopefully solidify my understanding. 

My favorite thing so far in this project is that I created a group of functions which became my design factory, they iterate through a list of CSS colors and another list of fantasy names to create the text on the buttons, so the user can click around and pick from 20 different color theme for the webpage. So far these functions live inside my index.js file (I am keeping them no matter what) but once I check out my new git branch I'd like to see if I can keep them by creating a Color or Design class to organize them instead of letting them hang in the index file. 




