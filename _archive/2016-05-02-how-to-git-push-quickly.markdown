---
layout: post
title: "How to Push Quickly to Remote using a Bash Alias"
date: 2016-05-02 12:48
comments: false
categories: git
---

# How To Push Everything to Git Quickly Using a Bash Alias

I do not recommend this technique to those who are learning git or intend to use it for large commits. I began to use this technique as a way to quickly push changes to README files or other text based projects.

## Before

That being said, this is what a workflow might look like for pushing even a small grammatical change to a repository.

```Bash
git add .
git commit -m 'make changes'
git push origin master
```

I found that doing this for even small changes could be a drag. So I began to chain theses commands together like so:

```Bash
git add . && git commit -m 'make changes' && git push origin master
```

## After
Still desiring speed, I created a simple bash alias that would do this for me. My workflow for minor commits now is as easy as this:

```Bash
pe
```

If you are unfamiliar with setting bash aliases, I would recommend looking into it some more. These come in handy as long as you are not using occupied aliases. One way to your bash alias may be like this:

```bash
sudo vim /bin/addcommitpush.sh
```

in  this text file, you simply add the commands you want to replicate each time the alias is called:

```
git add .
git commit
git push
```

then set the alias in your home folder by first calling:

```bash
vim ~/.bash_aliases
```

then writing the following (if there are already aliases set, just append to the end):

```bash
alias pe='/bin/addcommitpush.sh'
```

where "pe" is the alias that you would like to set (be sure to not overwrite or conflict with an existing alias). Now just source the .bash_aliases file so that the changes can take place immediately.

```bash
source ~/.bash_aliases
```

At this point, anytime you call this command, it should add, commit, and then push. Note that you still have to type in commit message in the default git editor. The amount of time that you save from this will probably equate to the same amount of time you spent reading this article. Happy engineering
