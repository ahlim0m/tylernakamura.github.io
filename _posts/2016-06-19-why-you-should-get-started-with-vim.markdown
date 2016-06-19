---
layout: post
title: "Why you Should Get Started with Vim"
date: 2016-06-19 13:43
comments: false
categories: vim beginners tutorial reasons
---

<img src="/images/vim-logo-transparent-background.png"/>

This post is directed at those who have never heard of vim or have had little experience with Vim.
Vim has an infamous reputation for its steep learning curve.
The terminal based text editor boasts an endless amount of arcane navigation commands and enough configuration to drive anyone crazy.
Nearly all other students I meet cower at the thought of doing all of there programming on the command line.
This being said, I think that if you are one of those wimps, you should reconsider and as least use Vim as a supplemental tool.
Below are my top reasons for Vim development:

Before we begin, first listen/read to this awesome monologue to set the mood: [Vim Creep - Norfolk Winters](https://www.norfolkwinters.com/vim-creep/)

### Brief History
Vim has a long history; at least for a text editor.
Vims roots lie in a similar project called vi.
Vim, sometimes called "Vi Improved" is a vi clone that was released in 1991.
Although, Vi was actually released in 1976.

### **Reason 1:** You have a workstation everywhere (Portability)
Working in DevOps, IT support and systems administration often entails working on a machine that is not your own.
Vi is guaranteed to work on all Unix systems.
I would also be really surprised to see a Linux system that doesn't have Vi or Vim.
When I used Eclipse, I would spent countless hours configuring my Eclipse setup.
Unfortunately, as soon as I needed to develop on another machine, my skills were rendered useless without my crutch.
Being comfortable with vi (or vim) means that you are also comfortable editing files that is Unix/Linux.
This boosts your credibility and usability when using SSH as well.

### **Reason 2:** Configurations can be easily shared (Portability)
As a vim user, you will create a ```.vimrc``` file in your home directory that will become your new best friend.
```.vimrc``` is responsible for nearly all of the configuration of vim. 
Anytime vim is loaded, it first consults the ```.vimrc``` and loads the text editor based on your preferences.
This functionality is awesome because this file can be easily shared or ported to all of your different machines.
At the time of this writing, there are almost [10,000 repositories on Github for vimrc files](https://github.com/search?q=vimrc&type=Everything&repo=&langOverride=&start_value=1)

### **Reason 3:** Development Speed (Speed)
For many, the potential increase in development speed is the primary reason for choosing vim as their go-to text editor.
If you listened/read the monologue mentioned above, the author paints a graphic picture of the potential of using vim.
I can't say that my skill-set is near that god-like state, but I know enough to know that learning vim is worth my time.
One of my favorite features of vim is that many of of the hotkeys are based on keeping your hands near the home-row.
Without engaging in the Emacs-vim rivalry, this is something that I think vim has a "one up" on Emacs.
Vim in general is designed for navigation speed, when working with large files, vim makes it especially easy to jump from line to line or search.
At first, developing in vim will be like chewing glass, but with enough practice, you will flying around the document like you never have before.

Courtesy of [XKCD](https://xkcd.com/), this comic often appears when the discussion of text editors arises:
<img src="/images/xkcd-real-programmers.png"/>

### **Reason 4:** Lightweight
Functionally, Vim and Vi are largely similar.
As a vim user, you should have no problem switching to vi and vice versa.
Both programs are extremely lightweight, and by that I mean in literal bits.
While there sizes may vary, I can assure you that they will be smaller than any graphical based IDE.
Now days, such a bonus is hardly important, but it is still worth mentioning.

### **Reason 5:** Vim is Free Software
Lastly, the vim project is free software.
By this, I mean free as in America and not as in beer.
While it has its own license, it still falls under the umbrella of approved software by the Free Software Foundation.
The license also allows for Vim to be compiled with GPL libraries according to [the official repository](https://github.com/vim/vim)

### Summary
It would be moot to write a how-to here, as there is abundant documentation and hotkey cheatsheets here on the web.
If you have vim installed, you can call:

```bash
vimtutor
```

and follow the tutorial to get the basic of vim.
Join the master race, code faster, support free software, welcome to Vim.
Happy coding!

