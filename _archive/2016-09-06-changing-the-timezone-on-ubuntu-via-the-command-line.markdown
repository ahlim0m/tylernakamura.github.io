---
layout: post
title: "Changing the timezone on Ubuntu via the command line"
date: 2016-09-06 11:02
comments: false
categories: Change time zone ubuntu
---

I travel a lot. This is how you change the time zone on Ubuntu via the command line as of 2016-09-06:

```bash
sudo timedatectl set-timezone HST
```

to list the timezones;

```bash
timedatectl list-timezones
```

[source](http://askubuntu.com/questions/3375/how-to-change-time-zone-settings-from-the-command-line)
