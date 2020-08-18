---
layout: post
title:      "RESTful outside the box"
date:       2020-08-18 14:57:51 -0400
permalink:  restful_outside_the_box
---


Rails is great and in my opinion it has a cool suggestive name. I think that this huge framework next to saving you a lot of time and repetative work with it's amazing generators and underlying magic also keeps you on the track of being restful and clear to other developers. As nice this is, it can also get quite challenging, because not everything fits in the RESTful box. I found myself adding duplicate actions to the same controllers, like a create and a githubcreate, or a regular index page but also a filtered index page. Of course they can be kept in the same actions but I prefer to have them crystal clear and separate. Though the problem is, that something that is very evident and intuitive for me (How couldn't it be? I'm the one who built it!) others might have completely different preferences. But Rails gives you the rails by making it difficult for you to not be RESTful.

Because of this, I faced the problem the other way around too: My project has four models (and I am planning on adding more) and I don't need all of the routes for all of them. I used the require_login helper method to make sure that people without logging in can't access routes.

```
def require_login
        return head(:forbidden) unless session.include? :user_id
    end
```

But what happens if someone is logged in but navigates to a route that I don't have because it doesn't really makes sense? For example, in my ticket booking application, there is not really a point in for users to see all of the users who use the same application. But when I typed in that URL, it gave me the No route matches [GET] "/users" page and all of the existing routes, that gave me some security concerns. After looking around on the internet I learnt that this is switched off in production mode, and also found a setting to switch it off in development. (It is strongly discouraged, but I wanted to see what it does.) 

In the config/environments/development.rb file, 

```
config.consider_all_requests_local = true
```

if you set this false, it doesn't show all of your routing information. But as I learnt, it is not something to be worried about at the first place. 

Another great thing coming from this project was that finally I am starting to see why is it awesome to write a method instead of just writing the code. In the beginning I haven't understand that why is it better to write 

```
def artist_name 
    self.artist.name
end 

```
somewhere very far in my code from the location where I could just call concert.artist.name. But having this huge filesystem and using this method in several views helped me see what makes this awesome. Because of the separation of concerns, I know where to find this method, in this case it is defined in the concert.rb file, since I was calling it on a concert object. It is easy to understand if I should look for something in a helper file, or in the model, or in a partial. After tracking down this source method I can easily change it without looking through all of my files, seeing where did I call what **on what.** Now it just feels right to see a dash instead of two dots. 

My scope methods are the following: 

```
scope :order_by_name, -> {order(:performer)}
scope :search_by_location, -> (chosen_location){where("location = ?", chosen_location)}
```

I wrote the first one just to make sure that my scope method for my search bar is chainable. If I understand it correctly, the scope method returns an activerecord relation, meanwhile a simple class method self.find_by returns a regular ruby array and you can't call multiple scope methods on it. 

I added a lot of simple validations, has_secure_password already comes with some, I set presence: true for almost everything.

```
validates :performer, :location, :date, presence: true
validates :location, uniqueness: { scope: %i[performer]}

validates :quantity, inclusion: {in: 1..6}
```

But what I found incredibly useful is this second validation. It validates the uniqueness of my concert locations in the scope of a performer. I wanted to make my rails application like a real world project. Of course that concert locations doesn't have to be unique and an artist often goes on a tour. So filtering it that way that an artist shouldn't have a concert twice at the same place seemed like a good validation. I will try to connect it with dates, since an artist might come back later to the same place, but it's a start. And the last validation was the one that I could quickly find and used range to make sure that it validates integers, and not the amount of characters.

```
validates :content, length: {minimum: 3}
```

One last thing is that I didn't add any style yet, because I still have the time to open a new branch on GitHub (ready to drown but excited to try) and I'd like to make the other side of the project: I'd like the user to be able to log in as an artist and create concerts with a nested form, so upon creation they can also add a comment, like "It will be fun like Rails!".



