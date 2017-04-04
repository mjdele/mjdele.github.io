---
layout: post
title:  "My Sinatra Event App"
date:   2017-04-04 18:33:01 +0000
---

Going into the Sinatra Portfolio Project, I felt a bit shaky on my grasp of join tables and 'has_many :through' associations, so I wanted to create models that utilized this relationship and put my understanding of it to the test.  As someone who enjoys finding and going to concerts of my favorite musical artists, I thought building an app to keep track of upcoming music events would be interesting to me, while also providing multiple models to keep track of.  There were User, Event, Venue and Performer models that all had to be tied together with the proper associations.  

Conceptualizing these relationships on a pad & paper, running the migrations, testing them in pry, making revisions, running new migrations, and retesting until I was finally comfortable with the results was quite the process for me.  And I ended up with a migration folder that reflected all of these iterations:

![](http://i.imgur.com/qUpxvDx.png)

But by then end, I had a complete understanding of how I wanted my models to interact, and I was much more comfortable working with 'has_many :through' associations.  

The process of building out the corresponding controllers and views for the project was a very familiar one, based on the numerous previous labs that covered this.  Creating a new route in the controller, connecting and developing the view, running 'shotgun', testing the code, revising, retesting, commiting the code.....and, repeat.  

Compared to my first project, I found myself much more comfortable revising my code and building helper methods on the fly to help with the overall readability. And by the end, I was very satisfied with the final result and the topics reinforced along the way, but also excited to move on to an even more powerful framework, Rails.
