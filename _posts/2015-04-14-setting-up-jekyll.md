---
layout: post
title: Setting up Jekyll
date: 2015-04-14 12:21
comments: true
categories: 
---

Three years ago when I initially setup [snail trail](http://projectsnailtrail.org), I did it as an [octopress](http://octopress.org/) site. Funny, when I opened the octopress site just now, I saw the latest post (three months ago) more or less started with the following quote:

> If I'm being harsh, I'll tell you that as it is now, Octopress is basically some guy's Jekyll blog you can fork and modify.

That's actually a big part of reason I was planning to migrate over to Jekyll. Maybe with the new release I'll want to come back, but when I looked into it recently, Jekyll seemed plenty sufficient to me. I just want a basic framework that lets me write posts in markdown and build them into a static site. Beyond that, I'd really like a static search index (so I don't have to rely on a google search bar) and it looks like [lunr.js](http://lunrjs.com/) has a plugin for jekyll that should handle that.

## Reproducible Virtual Environments

One thing I've gotten very used to over the last few years in my working life is using [vagrant](https://www.vagrantup.com/) to create easily reproducible development environments, then put all of the logic for creating those environments under source control repository for the development project they support. That way the development project not only includes the code to run, but also the target environment to run it on.

Eventually the snail trail site will end up in a git repo (actually, it already is, but I'm not sure I want to maintain that history since the majority of it would be octopress history...) and that repo will have a folder a number of configuration scripts (vagrant and some shell scripts for now) sufficient to build a development environment with all of the development prereqs (ruby, jekyll, etc). The best part of this approach is that I can throw away the environments and forget about them (until I need them again, if ever). I can install whatever I want and not worry about it leaving random garbage (entropy) on my real machine.

## Setting up an Initial Machine

I like to start with a stock image. There are plenty of prebuilt images on [Vagrant cloud](https://atlas.hashicorp.com/) (which has apparently been renamed atlas), but I'm not really sure where hashicorp is going with it and I generally prefer the approach of starting with something as basic as possible and scripting additions to it. One of these days I'll get around to learning chef, puppet, or one of them numerous other configuration management tools. For now I'm happy to get by with slightly less portable shell scripts. Even so, I like using chef's already hosted [bento boxes](https://github.com/chef/bento) for my stock images.

I'm going to start with an ubuntu environment, but I'll likely switch to a centos box if ubuntu doesn't happen to make a lot of the installation extra easy (somehow I have a feeling this community may favor ubuntu).

### Initialize the base box

```
vagrant init ubuntu-1404 http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-14.04_chef-provisionerless.box
vagrant up
vagrant ssh
```

### Manually provision it with Jekyll

I run the following as root (eventually it will end up in a `provision.sh` script that vagrant runs as root the first time it starts up the box).

```
sudo su
apt-get -y install ruby ruby-dev make gcc nodejs
gem install jekyll  --no-rdoc --no-ri
exit
```

> **Note,** it looks like you need to install gcc as a minimal prerequisite to building some of the jekyll gem dependencies. Also, the nodejs is apparently necessary at certain releases to provide a javascript runtime environment -- even if you don't use coffeescript. Skipping rdoc and ri doc speeds up the installation if you have no intent of using the doc.
 
### Create a test site

```
jekyll new test
cd test
```

### Update the Vagrantfile

So far everything may be working fine, but when we go to run

    jekyll serve
    
we won't be able to access the jekyll site from outside of our vagrant development environment. We'll want to use shared folders to both persist our site (as well as edit files using an editor outside of the vagrant environment) and to access it from our local machine's browser. We'll use shared folders for the former and a static ip address for the latter (port forwarding would work as well). I'll also go ahead and make the environment automatically reproducible by adding the manual provisioning steps into a `provision.sh` script file.

`provision.sh`

```
apt-get -y install ruby ruby-dev make gcc nodejs
gem install jekyll  --no-rdoc --no-ri
```

`Vagrantfile` (I've added, uncommented and/or altered the following lines to the main block)

```
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../../jekyll-sites", "/jekyll-sites"

  # Provision the box 
  config.vm.provision "shell", path: "provision.sh"
  #config.vm.provision "shell", path: "startup.sh", run: "always"
```

Now I have a reproducible environment that I can destroy and rebuild anytime I want automatically:

```
vagrant destroy
vagrant up
vagrant ssh
cd /jekyll-sites
jekyll new test
cd test
jekyll serve
```

> **Notice** that after I've done this, the test directory exists on my local file system because I created it in a shared folder. I should also mention that I had to create that folder locally before I started up the vagrant box or I would have received an error when I tried to start it up.

Now that Jekyll's serving the test site on port 4000, I should be able to navigate to it from my local browser at the vagrant boxes static ip [http://192.168.33.10:4000](http://192.168.33.10:4000).

### Connection Refused

Ugh. I hate it when this happens, because it could take anywhere from an hour to a day to too long to bother to diagnose and fix... I've hit this problem a number of times before, and eventually I'll resolve it enough times to just no better. In this case it was a matter of setting the host on the server side to `0.0.0.0` (listen for requests on all network interfaces) or `192.168.33.10` (only listen for requests on the network interface attached to 192.168.33.10`) rather than letting it default to `localhost` (which only listens to requests that come in locally).

```
jekyll serve --host `0.0.0.0`
```

Now we try navigating to the site from our browser again: [http://192.168.33.10:4000](http://192.168.33.10:4000).


 



