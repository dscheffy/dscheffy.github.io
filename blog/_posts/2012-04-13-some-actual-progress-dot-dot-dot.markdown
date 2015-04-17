---
layout: post
title: "Some actual progress..."
date: 2012-04-13 12:28
comments: true
categories: 
---
I know, I said I was going to make a point of saying a little something here every day to keep myself honest, and after two days I go off the radar... 

I'll admit, the rest of last week was pretty much a wash. Wednesday was a day of chores, and I spent all day Thursday and Friday at a mobile apps conference. I was worried this week would end up being more of the same -- Monday was a brilliant start (chores), Tuesday I actually lived up to my goal of leaving the house to work (and accomplished little more than updating my resume).  Then suddenly out of nowhere, the most amazing thing happened on Wednesday -- I sat down at home and lost myself in the code.  It was only for a few hours because I had to walk away from it to go meet with some people, but I didn't want to!  Rather than looking for any excuse to do anything except code, I suddenly just wanted to code.  

Thursday that's what I did.  I had a really dumb hello world app that did nothing more than register a `PendingIntent` with the `AlarmManager` to wake up a `BroadcastReceiver` every 10 minutes and start up a background `Service` which turns on the gps receiver and waits for a location update.  There's a bit of ugly logging and whenever it gets a location update, it rights it out to a file -- nothing pretty -- but something to hack around and explore with.  So I fired it up, and.....

**Nothing.**

Duh, I'm inside and gps signals don't penetrate walls all that well.  So I disconnect the phone from my laptop and go for a walk.  **Again nothing** _(well, nothing but 72% of my battery getting sucked up by an application which doesn't seem to be doing anythign)_.  It doesn't matter, somehow this has piqued my interest and now I'm hooked.  I'm sick of reading through all the doc, it's time to act -- it's time to use the number one trick of true hackers everywhere -- **trial and error**.  

However, I'm a little too nitpicky to just go around willy nilly changing lines of code.  I'd like to be able to go back to where I was, so let's thrown this all under version control.  It's still a throw away application, so I'm not going to put it up on GitHub for the whole world to see, but it would sure be nice if I could keep track of changes and their effects for my own purposes -- so I throw it all in a local git repo.  What's more, each time I make and test out a change, it would be nice to keep a record of the results -- git notes to the rescue!  

In the end, Thursday was a productive day of exploration.  Am I much closer to a finished application?  Not really, but I do have a much clearer understanding of what's going onwith the devices gps -- ok, clear would be an overstatement, but then again I didn't say _clear_, I just said _clearer_.  

What I do have is various incarnations of an app and an understanding of how turning on and off different combinations of wifi, network data packets and gps effect the quality of location data coming back.  I also have a better idea of why I never had much luck with my gps -- I didn't understand anything about **_almanacs_** and **_ephemerises_**.  The gps basically needs a chance to _warm up_ the first time you turn it on, and after that it starts up much faster.  Considering the fact that I usually have my GPS disabled, it's never had a chance to warm up and I've historically always given up on it before it's had that chance.  

Anyway, I still need to go through some more exploratory hacking (today I was watching what was going on with GPS satellite objects behind the scenes to get a better idea if I can avoid firing up the gps receiver if it looks like we're likely indoors).  I'm getting a better idea of the approach I think I need to take.  One thing that is becoming clearer is that this isn't the typical use case people have in mind when they talk about using geo-location on mobile phones.  Most of the commentary and documentation on the subject concentrates on writing applications which seem to quickly have a good idea of where you are right from the moment you open them.  The general trick to doing this is to piggy back on any other applications request for a location update -- that way when somebody opens your app, you know right away where they were the last time they did something that required knowing -- which for somebody using a geocentric app is likely relatively recently.  

I could write an app that is fully passive and only takes into account locations that come in from other requests (and in the end that may be one of the configuration options), but more likely we'll want to pick up motion data at check points when the user isn't interacting with the device (granted, I may be underestimating the power of passive location collection given how other people use their phones based on the fact that I don't use it at all on mine...)  I'll have to find a happy balance and beta test it with real world users eventually...

As for now, it's time to get back to hacking.  

