+++

title = "Vagrant: Setup development environments FAST!"
description = "Understanding the popularity behind Vagrant"
author = "Gurpreet Luthra"
date = 2012-12-16T02:13:50Z
images = ["/images/general/orange-evening.jpg"]
aliases = [
    "/2012/12/16/vagrant-an-interesting-approach-dev.html/",
    "/2012/12/16/vagrant-an-interesting-approach-dev.html"
]


tags = [
    "programming",
    "architecture",
    "technical",
    "devops",
]

+++

![Near the Norbulingka Institute, Dharamshala, India](/images/general/orange-evening.jpg "Near the Norbulingka Institute, Dharamshala, India")

If you have never heard of [Vagrant](http://vagrantup.com/), or are interested in understanding what is Vagrant, then this blog should be useful to you.

## The Need for Vagrant

Recently, I was involved in organizing the [GraceHopper Hackathon](http://gracehopper.org.in/2012/conference/hackathon/) in Bangalore where we expected about 50+ women developers to come and contribute to Humanitarian software projects like [OpenMRS](http://openmrs.org/), [RapidFTR](http://rapidftr.com/), and others. Since all participants would mostly be new to the projects, and we had a single day to get them going, and contribute -- we wanted to ensure that people spend as less a time on setup of their dev environment as possible.

I got introduced to Vagrant, because at the GraceHopper Hackathon, one of the projects - RapidFTR, provides people with the ability to [setup their environment using a Vagrant box](https://github.com/rapidftr/RapidFTR/wiki/Using-a-VM-for-development) -- and that's when I realized -- this is interesting!

Setting up a development environment for many projects now-a-days isn't a matter of simply running a script or downloading a piece of software. On most projects, the average setup time to get all up and running is usually a day, and sometimes more. Most often, time is spent on setting environment variables, handling software version conflicts, or general configuration. Not to mention, that once you are done, doing this for the next project would be even more challenging.

## Vagrant: The Solution

Vagrant provides an elegant solution to this whole mess.

In simple terms, Vagrant allows you to provides a "box" which has everything pre-installed and setup for you -- and all you do is "start" the box on your machine and you are set. This box is essentially a Virtual Box VM, which is running in invisible mode (background mode) on your machine, and has the whole development environment for your software setup inside it. But, instead of coding inside the Vagrant VM, you code on your laptop -- and do your builds, compilations and server startups, etc inside the Vagrant VM.

Vagrant essentially shares a folder on the "box" which is also available on your laptop, and this is the folder that contains the code of your project. Any modifications to that folder by your laptop (host), or the box (guest), will be reflected to each other.

Basically this means that your laptop owns the code, so you use your favorite powerful IDE and laptop environment to modify code, and you use the vagrant environment to "run" the code.

**The advantages you get when using a Vagrant box are:**

1. You don't install stuff on your machine, and mess your machine up with all the weird libraries and settings. All you have on your machine is the "code". Rest is inside the VM.
2. You have exactly the same development environment as everyone else in your team.
3. The development environment is created once (Vagrant box), and used everywhere on all Operating Systems. This is because the Box is essentially a VM, which is running on top of Virtual Box. And Virtual Box VMs can be run on any host operating system.

## Is it different from using a VM?

Some people ask the question -- why Vagrant Box? Why don't I just setup a Virtual Box VM and everyone can work on that VM. That is also the same -- isn't it?

Well the answer is -- "Almost".

If you create a VM, and then ask people to work on that VM on their machines -- you are in for trouble most of the time! In most cases a VM on your machine is slow. It is especially painful when you have to do things like editing, coding, etc. Plus that also means you have to learn the shortcuts of the VM to make you productive on that VM.

When using a Vagrant box, you aren't working in the VM. You are working on your own laptop, and only connecting to the VM in "ssh" (command-line) mode. In effect, you are actually just firing a few commands to VM -- like build, start server, etc and the rest of the work is being done on your own machine. For you, the Vagrant box is just like a "server" to which you connect and tell what to do.

A Vagrant VM is usually viewed as a light-weight command-line only VM which usually runs a Linux OS (Lucid32 by default, but you can use Ubuntu or anything else).

Vagrant also allows you to configure port forwarding, so that when you type a URL in your browser like http://localhost:3000, you get connected to your server application running inside vagrant -- just as-if the server was running directly on your laptop.

## Steps to setup a Vagrant Box on your machine

When you have a Vagrant Box based Development environment setup (like RapidFTR did), here is all you do to get yourself setup:

1. Install Virtual Box for your laptop. If you have a Mac, then you install Virtual Box for Mac (and so on). This will act as the environment inside which Vagrant box will run.
2. Install Vagrant for your laptop. Once you install vagrant, you will see that on command line "vagrant" command will become available.
3. You download the code into a folder on your machine (say from Github or your network code repository).
4. You "add" a vagrant box to you laptop using the "vagrant box add" command. This command will need the path to your vagrant box VM. Alternatively, the box can be downloaded and added automatically from the internet as part of the vagrant up command (in next step).
5. You then do a "vagrant up" to start your box. This vagrant "up" command is done from your code directory, and the code directory will contain a "Vagrant" configuration file with configuration details on the Vagrant box to run. If the box isn't found on your local machine, vagrant will attempt to download the box from the URL provided in the vagrant configuration file. (This means you didn't use the box add command to add the box locally - as was mentioned in the previous step).
6. Once the vagrant box is up and running, then you ssh into the Vagrant box using the "vagrant ssh" command (or putty on windows) -- to build/start/stop your project application.

That's it. Now you are free to modify code on your local machine, and see it working via the vagrant box VM environment.

## Chef your Vagrant

Vagrant also allows you to run [chef](http://vagrantup.com/v1/docs/provisioners/chef_solo.html) scripts as part of your vagrant up command. The chef scripts will perform the installation and setup of software inside your Vagrant box. This way -- the power of infrastructure automation and provisioning provided by chef, can be combined with the power of a decoupled development environment provided by Vagrant.

_Originally posted on my older blog post here: [Vagrant: An interesting approach to setup development environments FAST!](http://techie-notebook.blogspot.com/2012/12/vagrant-interesting-approach-to-setup.html)_
