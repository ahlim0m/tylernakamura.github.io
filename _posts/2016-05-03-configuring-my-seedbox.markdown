---
layout: post
title: My Seedbox Configuration and Guide
date: 2016-05-03 12:41
comments: false
categories: seedbox vps
---

(**Please note that the guide is currently incomplete and is being updated as I set up my seedbox 5/4/16**)

This post will act as a diary of my efforts in the configuration of my off-shore seedbox. Ease of use and scalability are my primary goals for this project.

I think that other guides are lackluster and dated. [This guide](https://harbhag.wordpress.com/2010/06/30/tutorial-using-rtorrent-on-linux-like-a-pro/) for example, fails to explain why the up and down speeds are set the way they are. 

I don't think that firefox extensions are neccessary either. I plan on changing the way Firefox handles magnet links with a link to a simple script that utilizes wget and ssh. This script just needs to ensure the that the VPS rTorrent gets a hold of the magnet link. The rest is history.

##### Select a VPS service

I chose to go with a VPS from [Dediseedbox.com](http://dediseedbox.com/). The fact that they are built towards seeding made me choose them as my provider. I also like d that the servers are located outside of the US. 

##### Set up SSH Keys

SSH keys allow a client to quickly log into a VPS without the use of a password. SSH keys can also enhance security if you choose to still use a password. [Digital Ocean has an excellent basic guide for setting up such keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

### Goals
- One click push magnet to VPS seedbox
- Automatic server side load balancing
- Email alerts about bandwidth caps and other KPIs

### External Resources
- [Guide for optimizing speed caps](https://torrentfreak.com/optimize-your-bittorrent-download-speed/)
- [Default rtorrent.rc config file from official repo](https://github.com/rakshasa/rtorrent/blob/master/doc/rtorrent.rc)
- [Digital Ocean - How to Set up SSH Keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)


