---
layout: post
title: "What Terminal Commands Do I Use the Most?"
date: 2016-05-11 15:20
comments: false
categories: Bash terminal script
---

When creating bash scripts, functions and aliases, it may be useful to display which commands are used the most as a percentage.
I found this handy script from [Digital Ocean](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions).

```bash
history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10
```

The output looks like this:

```Bash
 1  247  24.7%  cd
 2  112  11.2%  vim
 3  90   9%     exit
 4  72   7.2%   ls
 5  70   7%     xset
 6  56   5.6%   apt-get
 7  40   4%     vlc
 8  40   4%     rm
 9  38   3.8%   screen
10  27   2.7%   htop
```
