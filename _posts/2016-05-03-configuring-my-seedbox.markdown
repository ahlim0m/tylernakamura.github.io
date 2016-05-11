---
layout: post
title: My Seedbox Configuration and Guide
date: 2016-05-03 12:41
comments: false
categories: seedbox vps
---
Below is a guide and a tale of my efforts in creating an autonomous seedbox:

### Selecting a Virtual Private Server
I chose to go with a VPS from [Dediseedbox.com](http://dediseedbox.com/). The fact that they are built towards seeding made me choose them as my provider. Compare [their rates](http://dediseedbox.com/vps.html) to another popular provider like [Digital Ocean](https://www.digitalocean.com/pricing/). Having servers located outside of the US can also be advantageous for a variety of other reasons.

I was pretty satisfied with the internet speeds upon my purchase, especially considering for non-US location. For me, the speeds exceed sufficiency.

<img src="/images/speedtests.png"/>

### Set up SSH Keys
SSH keys can allow a client to SSH into a VPS without the use of a password. When configuring a VPS, you may need to log into your server often. Setting up keys can help speed up this process. SSH keys can also enhance security if you choose to still use a password. For more information, [Digital Ocean has an excellent basic guide for setting up SSH keys.](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

For maximum laziness and brownie points, set up a bash alias that allows you to type in a word to SSH into your VPS. For example, when I type:

```bash
go-to-holland
```

my bash alias automatically logs me into the VPS; all done securely without the use of a password.

For more info on bash aliases, [see here](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions).

### Configure rTorrent
"rTorrent is a text-based ncurses BitTorrent client written in C++, based on the libTorrent libraries for Unix, whose author's goal is a focus on high performance and good code." ~[source](https://en.wikipedia.org/wiki/RTorrent)

I have made rTorrent my client of choice as it functions via the CLI.

Much of the documentation that you need in configuring rTorrent can be found at the [Arch Linux wiki](https://wiki.archlinux.org/index.php/RTorrent). However, this segment will mostly pertain to what I consider to be the essentials in my rTorrent configuration.

My apt-get installation for didn't seem to include a copy of the **rtorrent.rc** config file (or at least I couldn't find it) so I have included a link at the bottom of this page to the official config file from the projects repo.

To download the config file from the command line:

```bash
wget https://raw.githubusercontent.com/rakshasa/rtorrent/master/doc/rtorrent.rc
```

I found a lot of the following information [from this blog post to be useful for configuring rTorrent](https://harbhag.wordpress.com/2010/06/30/tutorial-using-rtorrent-on-linux-like-a-pro/).

### Running rTorrent in the Background
I found that calling **rtorrent &** doesn't really work as I had hoped.
Finding [this solution on a forum](http://www.linuxquestions.org/questions/linux-general-1/problem-using-screen-cannot-open-your-terminal-'-dev-pts-0'-please-check-338313/) will describe how to run rTorrent in the background. Running the following commands will allow you to run rTorrent in the background:

```bash
sudo screen rtorrent
```

Then press ctr+a, then ctrl+d to detach from the screen.

Be mindful of the PID, in order to kill the process should you ever need to.

### Converting Magnet Links to .torrent Files
[In 2012, The Pirate Bay no longer offered torrent files but magnet links instead](http://www.webcitation.org/6BWzbw7JF). This decision provided another layer of abstraction in the hope that it would mitigate some of the litigious efforts to banish The Pirate Bay.
It also reduced the amount of bandwidth necessary to keep the site running through a proxy.
As a user, all you really have to know is that a magnet link stores meta data about a torrent file and it requires some minor conversion in order to retrieve the .torrent file that you need.
There are sites that allow you to do this conversion from a browser:

<a src="http://torrent-to-magnet.com/"><img src="/images/torrent-magnet-site-screenshot.png"></a>

However, I need magnet conversion from the command line, I [found a nifty script](http://snarvaez.com.ar/libertad/index.php/2013/05/10/download-magnet-links-with-rtorrent-from-command-line/) that helped me create this:

```bash
#!/bin/bash

[[ "$1" =~ xt=urn:btih:([^&/]+) ]] || exit;
echo "d10:magnet-uri${#1}:${1}e" > "meta-${BASH_REMATCH[1]}.torrent"

scp "$1.torrent" user@remote_host:/path/to/rtorrent-watch-file

rm $1.torrent
```

The script usage looks like this:

```bash
/script "magnet link here"
```

Note that the magnet link in this scripts usage needs to be surrounded by quotation marks.

## More Resources
- [Guide for Optimizing Torrent Speed](https://torrentfreak.com/optimize-your-bittorrent-download-speed/)
- [Digital Ocean - How to Set up SSH Keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
- [Digital Ocean - Bash Alias Tut](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)
- [Download Magnet Links with rTorrent From Command Line](http://snarvaez.com.ar/libertad/index.php/2013/05/10/download-magnet-links-with-rtorrent-from-command-line/)
