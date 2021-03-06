---
layout: post
title: "Instant Infrastructure on USB"
date: 2013-01-10
comments: false
categories:
---

I make my living as a Computer-Chef. People hire me to prepare many computers along with their desired software and make it all come together according to precise recipes. Like any chef, I like to prepare my recipes from scratch using only the finest ingredients. I also love sharing my recipes and teaching people to cook on their own.  

Preparing complex computing systems from scratch can be a pain... Where do you start? How do you know when you've added just enough to produce what you set out to accomplish? Myself I like to start with known good ingredients, and sample or test my concoction along the way.  

In the world of computing, the from-scratch cooking process usually starts with bootable software like a CD/DVD from a vendor that makes the software that all other software runs on top of... the operating system (aka OS). Microsoft and Linux vendors make their software available via a special file called an ISO that you can burn to a CD. Most of the time people boot those CD's and manually use a mouse and keyboard to answer questions related to installing the OS before they get around to adding their own software to run on top, and then may spend hours configuring. If they ever need to do a restore, they have to go through all that process again. Backups could help in restoring, but if you wanted to share the software and configuration that you use with a friend or a peer/professional it can be a bit harder.  

I started working for Opscode four months ago because they make a software called Chef (notice the capital C) that runs on top of _just the OS_ and it uses recipes to automatically install and configure any other software that you would want! Tying together installing the OS to the hardware and Chef to the OS all in one step is something we are starting to do fairly well in the cloud, but I often like to cook for friends in places where there might not be any internet.  

At Opscode I do a lot of Chef training. Teaching someone to cook without a kitchen is hard, so we developed a mobile teaching kitchen. My students connect to a special laptop that contains a mini-cloud with everything needed to spin up plenty of cloud-computers to teach the class. Setting up the laptop OS and software is quite a daunting task. I wanted it to be as easy as booting an OS CD and choosing a disk.  

Most bootable OS CD's run an installer that asks questions about what it should do. Luckily Windows and Linux allow you to provide a special file to answer to all the questions it might ask. There are also some hidden questions you don't see during a normal install like  'What commands would you like to run during stage X of the install?'. I've used these hidden options to run commands that install Chef and run recipes to completely automate the installation of Linux and Windows, including all desired software and configuration.  

I've done this recently on Windows using my [windows-fromscratch](http://hh.github.com/) code. However, I've also been using Linux for many years and like the idea of being able to give away working bootable USB's that can be used to deploy complex infrastructures from scratch. So I've distilled that process down into a few cookbooks containing the recipes needed to automatically create those sticks. I've created 2 cookbooks that are part of the :ii project.  

The first one is called [ii-usb](https://github.com/hh/cookbook-ii-usb). It starts by downloading and verifying the ISO for the OS (Ubuntu in this case), then formats a USB for booting and copies the ISO onto it. It then creates all the files necessary to pre-answer all the questions (except for which disk to format) and copies over Chef and any recipes I may want it to  use.  

The second cookbook is [ii-ubiquity](https://github.com/hh/cookbook-ii-ubiquity), during Ubuntu's install, it runs a program called Ubiquity. When the USB boots, it will run Chef with different recipes at different stages to configure such things as the boot-screen, background, wireless-passwords, hardware-specific drivers, etc. These can be configured by edited files on the USB stick (for now... I plan to provide a gui soon) and the only question asked is which drive to format.  

When the USB installer is done, the computer boots and runs Chef against a last set of recipes... in my case I have recipes for setting up the Opscode training laptop. I've recorded a 9:30 long video of booting an ii-usb created USB stick installing the training-laptop I created for Opscode. For dramatic effect I switch to a black screen to show when Chef is running the recipes.  

[http://ww<wbr>w.youtube<wbr>.com/watc<wbr>h?v=Fauka<wbr>aVwm2c](http://www.youtube.com/watch?v=FaukaaVwm2c)  

While none of this yet requires any other computers or internet, I see a possibility of booting a first computer with the stick that installs Chef Server and then boots / installs the rest via a local network. This is getting us closer to true instant infrastructure. Come hang out with us on our [Forum](https://groups.google.com/forum/?fromgroups#!forum/ii-discuss) and lend a hand to bringing infrastructure to classrooms, libraries, clinics and hospitals all over the world.  