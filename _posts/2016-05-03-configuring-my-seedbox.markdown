---
layout: post
title: My Seedbox Configuration and Guide
date: 2016-05-03 12:41
comments: false
categories: seedbox vps
---

This post will act as a diary of my efforts in the configuration of my off-shore seedbox. Ease of use and scalability are my primary goals for this project.

I think that other guides are lackluster and dated. [This guide](https://harbhag.wordpress.com/2010/06/30/tutorial-using-rtorrent-on-linux-like-a-pro/) for example, fails to explain why the up and down speeds are set the way they are. 

I don't think that firefox extensions are neccessary either. I plan on changing the way Firefox handles magnet links with a link to a simple script that utilizes wget and ssh. This script just needs to ensure the that the VPS rTorrent gets a hold of the magnet link. The rest is history.

I chose to go with a VPS from [Dediseedbox.com](http://dediseedbox.com/). The fact that they are built towards seeding made me choose them as my provider. I also like d that the servers are located outside of the US. 

### Goals
- One click push magnet to VPS seedbox
- Automatic server side load balancing
- Email alerts about bandwidth caps and other KPIs

### External Resources
- [Guide for optimizing speed caps](https://torrentfreak.com/optimize-your-bittorrent-download-speed/)
- [Default rtorrent.rc config file from official repo](https://github.com/rakshasa/rtorrent/blob/master/doc/rtorrent.rc)


