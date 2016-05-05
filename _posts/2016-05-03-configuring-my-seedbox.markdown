---
layout: post
title: My Seedbox Configuration and Guide
date: 2016-05-03 12:41
comments: false
categories: seedbox vps
---

(**Please note that this page is currently incomplete and is being updated as I set up my seedbox 5/4/16**)

This page will act as a diary of my efforts in the configuration of my off-shore seedbox. Ease of use, automation and scalability are my primary goals for this project.

I don't think that firefox extensions are neccessary either. I plan on changing the way Firefox handles magnet links with a link to a simple script that utilizes wget and ssh. This script just needs to ensure the that the VPS rTorrent gets a hold of the magnet link. The rest is history. Keep it simple, stupid.

### Select a VPS service

I chose to go with a VPS from [Dediseedbox.com](http://dediseedbox.com/). The fact that they are built towards seeding made me choose them as my provider. Compare [their rates](http://dediseedbox.com/vps.html) to another popular provider like [Digital Ocean](https://www.digitalocean.com/pricing/) Having servers located outside of the US can also be advantageous for a variety of other reasons. The VPS you choose really doesn't matter as long as you have root access.

I was pretty satisfied with the speeds that I got, especially for an out of US location. The speeds will vary based on the location of the download/upload but for my purposes, the speeds exceed sufficiency.

<img src="/images/speedtests.png"/>

### Set up SSH Keys

SSH keys can allow a client to SSH into a VPS without the use of a password. SSH keys can also enhance security if you choose to still use a password. For more information, [Digital Ocean has an excellent basic guide for setting up SSH keys.](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

For maximum laziness and brownie points, set up a bash alias that allows you to merely type in a word to SSH into your VPS. For example, when I type:

```bash
go-to-holland
```

my bash alias will recognize that as a command and automatically log me into the VPS; all done securely without the use of a password.

For more info on bash aliases, [see here](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)

### Configure rTorrent
"rTorrent is a text-based ncurses BitTorrent client written in C++, based on the libTorrent libraries for Unix, whose author's goal is a focus on high performance and good code." ~[source](https://en.wikipedia.org/wiki/RTorrent)

rTorrent is my client of choice as it primarily functions via the CLI; it also allows for detailed configuration.

Much of the documentation that you need in configuring rTorrent can be found at the [arch linux wiki](https://wiki.archlinux.org/index.php/RTorrent). However, this segment will mostly pertain to what I consider to be the essentials in my rTorrent configuration.

My apt-get installation for some reason didn't include a copy of the **rtorrent.rc** config file (or at least I couldn't find it) so I have included a link at the bottom of this page to the official config file from the projects repo. 

To grab the config file from the command line:

```bash
wget https://raw.githubusercontent.com/rakshasa/rtorrent/master/doc/rtorrent.rc
```

I found a lot of the following information [from this blog post](https://harbhag.wordpress.com/2010/06/30/tutorial-using-rtorrent-on-linux-like-a-pro/).

## Goals
- One click push magnet to VPS seedbox from Mozilla Firefox
- Automatic server load balancing, no task should consume resources that other higher priority tasks need
- Email alerts about bandwidth caps and other KPIs

## External Resources
- [Guide for Optimizing Torrent Speed](https://torrentfreak.com/optimize-your-bittorrent-download-speed/)
- [Default rtorrent.rc config file from official repo](https://raw.githubusercontent.com/rakshasa/rtorrent/master/doc/rtorrent.rc)
- [Digital Ocean - How to Set up SSH Keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
- [Digital Ocean - Bash Alias Tut](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)
- [Download Magnet Links with rTorrent From Command Line](http://snarvaez.com.ar/libertad/index.php/2013/05/10/download-magnet-links-with-rtorrent-from-command-line/)


