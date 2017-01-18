---
layout: post
title: "Building my Home Server (NAS)"
date: 2016-11-04 10:01
comments: false
published: True
categories: nas freenas freenas10 freenas9 esxi cloud home server lab ubuntu
---

# POST IS CURRENTLY UNFINISHED - WORK IN PROGRESS - 2016-11-04

To build a NAS for myself, I had a few important goals in mind:

 - Redundant Storage
 - As much NIX as possible
 - Offsite Backups
 - Low Power Consumption

## My Software

FreeNas felt like the obvious choice for my OS solution as it is ubiqitous and seemed the have the enterprise scaling capabilities. After a little research I saw that FreeNas10 was in the works. I saw the [State of the Union videos](https://www.youtube.com/watch?v=FzyMAGbp6_g) and fell in love with the UI. I also really like their move to incorporate a hypervisor and Docker support.

My goal was to have some kind of hypervisor available in the local network so I at first thought I could run ESXI and then virtualize FreeNas10. I realize that this may be foolish considering the FreeNas10 is not even out of beta, and I was virtualizing a hypervisor. I did actually get it to work after a lot of trial, but I found that a few things didn't work.

FreeNas10 as an instance of ESXI:

- Docker not working (although I don't think it was working for anything at point, virtualized or not)
- VMs in FreeNas10 couldn't be created
- Storage to FreeNas10 volume is reallllyyyy slow (I am talking 5mb/s)

I didn't really tinker with that setup too much after that to be honest, I knew that what I was doing was a little too arcane. I decided to then run FreeNas10 natively, and hopefully get my HyperVisor functionality from FreeNas10. Installing FreeNas10 was a breeze, even without official docs out. I played with it for a bit, but finally decided to go to FreeNas9 for the reasons below:

Reasons for FreeNas10 back to FreeNas9:

- Some funky things were happening with creating instances and GRUB
- Had some difficulties with NFS mounting. I saw that they were still squashing bugs with the NFS.
- Docker support not quite there yet
- Only supports Chrome browsers at the moment.
- Every nightly update would change my active boot option to a non-working one (this could have been my fault, but I couldn't fix it myself)

Don't get me wrong. FreeNas10 is freaking awesome, and I am so excited for the official release, but they are little farther away from official release than I thought they were.

2017-01-17 Update:

I once again changed my mind about the OS of the NAS, but this time I feel fairly confident in my decision.
Now I am just running Ubuntu Xenial with a Samba server set up. I don't need all the features that FreeNas9 has and I would prefer to change stuff over the command line.
There were just a few more things that I needed my box to do than NAS and I am not comfortable enough to leave the Debian based distro.
For example, If I wanted to have a cloud based hypervisor, I would have to open a port on my private network to let my cloud instances in.
Poking a hole in my network is not something I am willing to do especially considering that I don't have a static IP.

## My Hardware

As is common with most home NAS setups, my hardware consists of parts that I have lying around from previous builds.
