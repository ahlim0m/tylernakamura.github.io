---
layout: post
title: My Seedbox Configuration and Guide
date: 2016-05-03 12:41
comments: false
categories: seedbox vps
---

This post will be a diary of my efforts in the configuration of my offshore seedbox. Ease of use and scalability are my primary goals for this project.

I think that other guides are lackluster and dated. [This Guide](https://harbhag.wordpress.com/2010/06/30/tutorial-using-rtorrent-on-linux-like-a-pro/) for example fails to allow for optimized up and down speeds.

I don't think that firefox extensions are neccessary either. I plan on just changing the way that the Firefox Browser handles magnet links with a link to a simple script using wget and ssh. All it really has to do is ensure the that VPS rTorrent gets a hold of the magnet link. The rest is history.

### Goals
- One click push to VPS seedbox
- Automatic server side load balancing
- Email alerts about the bandwidth caps and other related KPIs

### External Resources
[Guide for optimizing speed caps](https://torrentfreak.com/optimize-your-bittorrent-download-speed/)
[Default rtorrent.rc config file from official repo](https://github.com/rakshasa/rtorrent/blob/master/doc/rtorrent.rc)


