---
layout: page
title: Project Backlog
---

1. Organize my stuff (figure out how to create a search index of my stuff)
2. Get everything under version control with backup -- git-annex maybe?
3. Renew projectsnailtrail.org (or find a better domain)
    * Done -- account good through 2017
    * read this -- https://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names
    * Update cname, mx records and any other ones that make sense in order to:
        * forward emails somewhere I can use (i.e. gmail or beaker)
        * allow me to use some subdomain to log into beaker (instead of my dyndns url)
        * move the snailtrail website over to a different host         
4. Upgrade octopress site
	* Let's stop hosting this on s3 -- run it on beaker (or maybe drbunsen -- ha ha ha ha) or github pages
	* Switch over from octopress to jekyll
	* install the [lunr.js](http://lunrjs.com/) [plugin for jekyll](http://10consulting.com/2013/03/06/jekyll-and-lunr-js-static-websites-with-powerful-full-text-search-using-javascript/)
	* Look into js-git (or is it git.js?) -- my dream would be to host a git repo as a static read only site (ideally with no preprocessing necessary) and provide a github like browsing experience -- all done on the client/browser side with javascript. I don't necessarily need `diff` level capability, but basic browsing of current state and historical state along with some nice formatting of markdown readme files.
5. Get into the flow of _blogging_ everything. 
    * This todo list (items should link to blog categories)
    * Figure out how to create a private realm too -- don't necessarily want everything to be public
        * This could just be a matter of two separate blogs -- and one is just hosted internally/locally on my home server and not available elsewhere
        * Or it might be nice if it just required auth so I could easily invite others to it (i.e. Karen for managing me, friends for collaborating)
6. Put _**EVERYTHING**_ (including this list) under source control
    * that doesn't necessarily mean github -- I don't want to pay for private repos
    * either just simple git repos, or maybe use gitolite or gitlab 
7. Get a raspberry pi
	* and maybe a few other toys
	* speaking of which, lets set up a formal budget for stuff like that
	* wouldn't it be nice to have a hardware development lab...
8. Investigate virtualization options -- not just vagrant. It would be nice to emulate something like openstack, but beaker may not have the hardware for it.
	* Just got bunsen -- a modern dual core desktop with 4gb of ram, so it should be able to handle a decent setup
	* Look into different options for baremetal virtualization -- Qemu, KVM, Xen? Openstack? 
9. Break out this todo list into the following (or more) categories
    * not started (these would have no blog entries)
    * ongoing (this would link to a category used for any blog entries, or some kind of project page)
    * retired (these would still link to old work, but they would either be completed or abandoned)
10. Build a prototype of my travel security gadget
    * how to build a prototype -- cnc lathe, mill, 3d printer?
    * what CAD software to define it? FreeCAD?
11. Revisit my old idea for representing visual images as logarithmic spiral coordinates
    * use R to build a quick conversion from cartesian coordinates to log-spiral and back
    * build a couple visualizaions of what's lost/gained in the conversion
    * build some basic classifiers for identifying shapes
12. Setup a network bootloader
	* look into PXE -- is this what it uses?
13. Cleanup and publish my matrix multiplication SVG illustrations
	* could I build this into a quick visual matrix multiplication calculator? You fill in the values of the matrices and enter and then watch it do the work? 

## Wish List / Shopping List

1. Software Defined Radio antenna -- sdr-rtl http://www.adafruit.com/products/1497
2. Raspberry Pi 2 B
3. More memory for dr. bunsen
