---
layout: post
title: "Some semblance of a UI is taking shape"
date: 2012-04-16 16:21
comments: true
categories: 
---
Friday night and Saturday I started adding a basic user interface to the prototype.  I'm not much of UI/UX guy and in my mind, this isn't really intended to be an application that people interact with -- it should just run seemlessly in the background without sucking up your battery like a vampire.  From a developer's point of view though, it's really a pain if the only way I can test it out is to hook it up to my development computer and view a log trace.  So Friday night I ventured into the android world of layouts and basic views/activities.  What started off as an application with one screen and two buttons -- `start` and `stop` has now evolved into an app with a second tab that displays a list of your historical locations.  I'm using a `ListView` and each item is simply showing the `toString()` value of a `TrackPoint` object (my own custom minimized version of a `Location`).  

Now I get a general idea of what's going on while on the road -- no need to plug into my computer and `cat` the file I'm persisting data to.  So far I've notice a few things -- the GPS actually works better indoors than I would have expected -- supposedly I was getting hits inside Costco, a Discount Wine Warehouse and one of my friends apartments (maybe I just don't get a signal in mine because it's halfway underground).  More importantly, Latitude and Longitude readouts don't do a lot for me and I'm sick of confirming the data by typing them into Google Maps =) 

Therefore as much as I'd like to jump into some serialization and battery utilization improvements, I think the next most important thing to do is probably add a MapView tab that plots the historical points on a map rather than just spitting out a list of Latitude and Longitude -- that will make verifying the integrity of the data much easier.  Additionally, I imagine it will be nice for eventual users (the ones that I'd like to say should be able to install it and forget it) to get a nice warm and fuzzy feeling from seeing a visual display of just what it is they're donating.

Fortunately Google makes plotting points ona map a relatively painless undertaking (or so I've been lead to believe).  I'm going through the exercise right now, but so far have run into a minor roadblock -- installing the api...  As far as I can tell from the documentation it looks like I may just need to update my sdk.  I'm in the process of downloading updates and with any luck I'll be able to get back to development in a few minutes once the download is completed.

To be continued...
