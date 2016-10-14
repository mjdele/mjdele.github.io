---
layout: post
title:  "The Election CLI Gem"
date:   2016-10-14 19:53:22 -0400
---

For the better part of the summer, I was somewhat obsessed with the website [FiveThirtyEight.com](http://FiveThirtyEight.com).

More specifically, I was focused on this:

![](http://i.imgur.com/Dw5BxzB.png)

The heated (to say the least) election had its hooks in me, and this is where I would go for a cooled-down, unbiased look at where things stood.

The [FiveThirtyEight 2016 Election Forecast ](http://projects.fivethirtyeight.com/2016-election-forecast/) collects hundreds of state & national polls, weights and averages them, and combines them with demographic and current economic information in an effort to forecast the presidential election.  It continuously updates as new polls come in, so it changes just about hourly.  In addition to providing a national forecast, the model also allows you to drill down and see the projected winner for each individual state (plus, D.C.).  

So when it came time for my CLI Data Gem Project for Learn, I was excited to have an idea that (1) fit the project and (2) I was very interested in (almost as important though, I now had a rock-solid excuse to constantly check the forecast :)

But with my idea in hand, I was confronted with this:

![](http://i.imgur.com/Y9kYvkD.png)

A fairly terrifying sight, considering I'd never started a project from scratch.  

But then I learned about the magic of typing this into my terminal:

![](http://i.imgur.com/eylVtaV.png)

Now with bin, lib, and spec directories established, as well as a README and Gemfile, things were starting to look much more familiar.  I still needed to get clear on my understanding of require, require_relative, require_all, $LOAD_PATH, etc.  Having spent almost all my time writing code in the lib directory with the previous labs on Learn, the hardest part of the project seemed to be trying to gain a more holistic understanding of how a program is put together.  But after more than a few viewings of Learn's video walkthroughs on environments, dependencies, and the like, I felt ready to start writing my code.  

Probably the most helpful analogy I picked up in one of the Learn video walkthroughs was that of thinking of your program like a line of dominos that are set up and waiting for the first one to be tipped over.  Having this image in my head really gave my process a much needed linearity.  What was the first domino I needed to set up?  

```
#!/usr/bin/env ruby
require './lib/election_cli_gem'

ElectionCliGem::CLI.new.call
```

And this pointed to the next domino, my CLI class:

```
class ElectionCliGem::CLI
  def call
    national_poll
    state_breakdown
    bye
  end
```

Which pointed to three more dominos: #national_poll, #state_breakdown, & #bye.  These would in turn lead me to setup my Polls class, and after quite a bit of time (with countless errors in between), I had a working CLI interface:

![](http://i.imgur.com/6GA5rZV.png)

But I had a Polls class that looked like this:

![](http://i.imgur.com/rEpfvCL.png)

This wasn't sitting well with me.  

My Polls class was doing too much.  It was scraping for the national and state polling information and also generating the CLI string output that the user sees.  These two actions seemed like they belonged elsewhere.  It also wasn't doing probably the one thing it should be doing: creating **permanent** poll instances for each state and saving the democratic and republican likelihood of victory.  

More refactoring...

![](http://i.imgur.com/fxAMdOM.gif)

And soon I had a Scraper class that did my scraping, a Polls class that created and saved all of my national and state polling forecasts, and a CLI class that pulled from both of these classes and generated the outputs that the user sees.  

My code was much more readable as a result, and my CLI interface was A LOT quicker.  Before the refactoring, each time the user typed in a state name, the gem pinged the website and scraped the appropriate data.  So 10 state queries equaled 10 website pings, and this slowed things down considerably.  Now, before any state queries are made by the user, all of the state polls (plus D.C.) are instantiated and saved in an array with just one website scrape, so the response time to a user's state query is instantaneous.


# Conclusion

This all was a lot of hard work.  

I would sum up my overall experience like this: Getting comfortable with being uncomfortable.

While it is incredibly daunting to almost constantly have a question about something new you've encountered, you learn quickly that the answers are out there.  Someone has already had that exact question and someone else has answered it on a message board or there is an entire blog written about it (in addition, of course, to all of the very helpful Learn instructors and students).  

And you eventually get used to the cycle: something new --> stuck --> research/ask questions --> understanding.

And then you move on....to something new.








