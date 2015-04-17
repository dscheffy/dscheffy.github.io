---
layout: post
title: "The Code is Up!"
date: 2012-04-26 18:04
comments: true
categories: 
---
For anybody interested in seeing just how shameful my current coding standards are, feel free to go straight to the [source](https://github.com/dscheffy/projectsnailtrail) -- I've finally uploaded it on [GitHub](http://github.com) and added a link to it in the navigation bar of this site (see the `Code` link above). I cleaned it up a little bit before uploading it, but that doesn't really matter since I didn't rebase all my commits -- It felt more honest to leave the full history.  As such, anybody can go back and see the complete evolution from what was once a project titled HelloJefferson to the current (and future current) state.  

For those geeks out there who are interested in giving it a test run on your device, you can go through the headache of building it yourself from the source (sorry, there's limited help in the README.markdown file) or you can just install the debug signed apk file on the project's downloads page.  It doesn't really do much -- there's two tabs, one with enable/disable buttons and one with a list of trips (which would be empty until you enable it for the first time and start tracking yourself).  At the moment it just tracks your locations in a `loc_tracker` on your sdcard (so if you don't have an sdcard on your device you'll probably get an error).  

I don't recommend trying it out, but if you're a real masochist and feel like getting involved, my phone's a froyo and I haven't tested it on anything else (it shouldn't work on anything lower than froyo, but I wouldn't mind hearing how it works on more recent systems like gingerbread).  

I haven't really gotten around to my next steps (that's actually what prompted some of the refactoring/cleanup).  It's always easier to build on a smaller base so I thought it made sense to delete all the ugly excess lines of code that weren't doing anything and comment some of the ones that were.  I'm also still dubious about this whole `cached` `networkLocationSource`.  Even after putting in logic to ignore those incoming locations, I was still seeing network provided locations that would jump back to old fixes.  Unfortunately I wasn't logging any extra debug information so I had no way of seeing the extra meta information associated with those erroneous points (I only know they came from the network provider because they show up as green on my display).  However, since adding the extra debug log, I haven't seen the issue again so I'm half wondering if I was just running an old build at the time.   

That's it for now.  Time to make some dinner -- nom nom nom nom!
