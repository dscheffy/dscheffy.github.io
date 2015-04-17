--- 
layout: post
title: "A day at the library"
date: 2012-04-03 14:55
comments: true
categories: 
---
![Harold Washington Chicago Public Library](/images/photos/2012-04-03.14.30.15.jpg  )

I had two [meetups](http://www.meetup.com) today -- one in the morning and one in the evening so I decided to spend the day downtown rather than going all the way back home. I've been saying I need to get away from the distractions at home and while this definitely does that, I suppose there will always be some distractions where ever I go.  

Yesterday I mentioned that developing a simple android app has turned out to be a less trivial exercise than I thought it might be.  Allow me to elaborate -- some of this probably has more to do with me and my apparent insistence on making life harder than it really has to be.  That's one way of putting it, but a nicer way would be to say that I prefer to put in a little (or a lot) of extra work at the outset of a project to prevent myself from having to do quite as much rework later on.  For instance I consider version control an absolute necessity -- there are plenty of options, but I plan on using `git` and considering this is an open source project, [GitHub](http://www.github.com) seems as good of a public repository provider as any.  I've never hosted a project on GitHub before though, so as a new user there's always a little bit of a learning curve.  

Now here's where me being anal comes in -- I realize it's always possible to reorganize your projects folder structure after the fact, and git especially does a good job of tracking changes and making it relatively painless to do, but I generally prefer to start a projects repository from a relatively well organized skeleton of files.  Any software development project will include a mix of source files (those that should get checked in) and generated output files (those that shouldn't get checked in) not to mention the development tools themselves and files necessary to configure the local development environment.  When you're new to a programming language, learning the syntax of the language is often the easiest part.  I find the difficult part (especially because it's often the worst/least documented) is learning the best practices in regards to effective folder structure (frequently because the development community is continuously evolving better best practices/conventions).  

I usually end up deploying a few 'hello world' applications before I really get a good feel for how to structure a skeleton app in any framework I'm new to.  In this case we're actually talking about a project which consists of one or more web service apps, at least one mobile app (android for now, but if things work out I'd hate to restrict it to android users), and then the site itself.  Part of me wonders if it's best to house them all as subfolders (or submodules) of a larger project repo, or if I should just keep them in separate repositories.  

Ok, enough ramblings for the day.  Time to do some actual coding...


