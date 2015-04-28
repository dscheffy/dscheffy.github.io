---
layout: post
title: "Small Data"
date: 2015-04-24 10:05
comments: true
categories: data
tags: vagrant virtualization excel sql sqlite r rstudio
---

I was analyzing some data for a friend earlier this week -- not my data, and not public data, so nothing for me to really talk about. That doesn't mean I can't talk about how I did what I did.

## Encryption

Since it was essentially client data, I wanted to treat it with the utmost discretion in terms of security and privacy. The hard drive on my laptop isn't currently encrypted (I know, shame on me), so I went ahead and [created an encrypted thumbdrive with a LUKS partition](http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/).

## Excel vs SQL

The data's small, the kind of data most people would an excel spreadsheet to work with, except that I'm not most people. It's not that I hate excel (or any generic spreadsheet tool), I use spreadsheets to do quick calculations or even a basic plot, but I rarely save the results when I'm done. It's mostly that I don't like the reproducibility or the certain lack of testability (or maybe transparency) that you get with a spreadsheet. Also, pivot tables have come a long way, but I tend to prefer a sql style group by statement.

As a first step, I went ahead and created a vagrant development box with `sqlite3` installed and imported the data. I wasn't sure if `sqlite` would really be sufficient for my needs, but it was pretty much the lightest weight place to start. `MySQL` or `MariaDB` would probably be the next step up if `sqlite` didn't meet my needs. I also wanted to get a little bit of hands on experience with `sqlite` since it's the _database_ of choice for _local storage_ in both browser and mobile based applications.

Vagrant was of course nice, because it made it easy to store both the virtual environment and the data all together in one place on that encrypted thumb drive.

## Analysis in R

Relational databases are nice for joins and aggregations, but when it comes to the final analysis of the data, I generally prefer a tool like R. Actually, given how small this data is, I could probably do most of the aggregation itself in R (it's just not what I'm used to from my _big data_ background). 

I really like Rstudio for performing adhoc analysis in R. It works well with a workflow that involves writing some commands in an interactive shell until something works, then selecting the lines from your history that actually worked and pushing them into a reproducible script that you can replay in the future.

The only problem I have with Rstudio is that it's a gui application and gui applications don't really work well in my world of vagrant based reproducible environments. I know, virtual servers don't have to be headless -- but honestly, I don't want to deal with X11, RDP, Citrix or anything like that at this point.

Instead, I'd like to check out Rstudio Server, which offers a web based version of Rstudio. I've heard about it before, but I've never seen it in the wild, so I have no idea how the WebUI compares to the GUI version. If I don't like it, I'll probably just fall back on installing the GUI version everytime I get a new laptop/desktop. If I _**do**_ like it, then my days of installing yet another native application may be over!

