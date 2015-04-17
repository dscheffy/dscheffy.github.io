---
layout: post
title: "A working map pane!"
date: 2012-04-17 14:31
comments: true
categories: 
---
It works!  It's ugly, slow and the code is absolutely horrendous, but when I finally opened up that map pane and zoomed in to see lots of little android images mapping out everywhere I went yesterday, I have to admit it definitely filled me with one of those warm and fuzzy feelings I was talking about!

That being said, I can't believe it took the better part of a day to implement.  The code really isn't that complicated.  The frustrating part was getting all of the dependencies set up in my development environment.  Here's what I don't get -- the "Google APIs add-on" has to be over a year old -- I people asking the same questions back in 2010 on Stack Overflow.  So why is it that somebody who installed his development environment within the last two months has to find the secret back door to run the correct update in order to get his development environment working?  This really shouldn't be that difficult!  Or at least it should be part of the basic installation instructions -- "Upon installing the tool, make sure you perform the following steps to update to the latest version as the version you've just installed is two years out of date".  

Sadly at this point I'm not even certain which of the steps I took were necessary to get it working.  I use Eclipse for development (that's where I do my actual coding), but then I use the command line to build and deploy projects (ideally since my intent is that this will be an open source project, I don't want to dictate what development environment coders user, so the command line is the least common denominator and the best approach for builds).  All the [doc](http://code.google.com/android/add-ons/google-apis/maps-overview.html) said I needed to type was:

    android list targets

Then locate the "Google APIs" target and update your project to use it.  Great, what if I don't see "Google APIs" in that list?  I did a few more google searches and they all led back to this same page.  It was starting to remind me of Microsoft's standard help menu where all you want to know is how to open the XYZ dialogue and the XYZ dialogue help entry starts with "To use XYZ, go to the XYZ dialogue..." huh? Really? If I knew how to do that, do you really think I'd be here?

Anyway, I eventually came to the next frustrating [page](http://code.google.com/android/add-ons/google-apis/installing.html) which was similar, slightly more informative, and much less comprehendible.  Apparently all I needed to do was "locate the Google APIs Add-On in the Android SDK and AVD Manager window under that component name Google APIs by Google Inc." (sounds familiar) "As shown in the figure below" -- contrary to popular thought, a picture is not always worth a thousand words -- especially when the picture you show isn't representative of what I see on my screen.

Clearly before selecting the target, I need to install it, so how do I install it when it isn't in the list of available targets to install...

Somewhere (I think [here](http://developer.android.com/sdk/eclipse-adt.html)), I finally came across a page that told me I may need to update my eclipse plugin by going to **Help > Check for Updates** and this miraculously fixed things.  Well, kind of -- I think I had to run it a few times but then again I was at a starbucks on a slow connection and disconnected before completing the update so had to restart it after reconnecting at home.  Here's what I don't understand -- why did I have to update my eclipse plugin?  What if I wasn't even using eclipse?  How would I have updated my sdk tool from the command line?  And again, why did I need to?  Did these APIs just come out within the last two months? 

This is the kind of stuff that had me shying away from android development in the first place.  I can't wait to see how much more of that kind of fun I have to look forward to in the near future!  At least for now I have something working and I can get moving with my next steps -- isoloating trips and reducing the "polling" rate when not on the move to improve the batteries life.


 
