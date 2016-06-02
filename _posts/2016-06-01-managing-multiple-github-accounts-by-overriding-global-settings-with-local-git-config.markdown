---
layout: post
title: "Managing Multiple Github Accounts By Overriding Global Settings with Local Git Config"
date: 2016-06-01 23:17
comments: false
categories: Multiple github accounts global local git config
---

I have a personal Github account that I use for personal projects, school work and even some work-based projects. 
At a place of employment, I have been required to create an entirely new Github account, for work strictly done with this place of employment. 
This new account is a pain, but it makes sense when you consider possible IP/patenting issues that could arise by blurring the line between personal projects and work funded projects.
However, I still need to be able to push to my personal account for personal tools that are not tied to a place of employment.

This post was inspired by this [Stack Overflow](http://stackoverflow.com/questions/9347458/switch-between-user-identities-in-one-git-on-one-computer) issue and has helped me find a simple solution for managing multiple Github accounts.

When configuring your ssh keys and the intial set up of git on your local machine, you probably were instructed to enter the following commands:

```bash
git config --global user.name  "Bob Alison"
git config --global user.email "person@example.com"
git config --global core.editor vim
```

In doing so, you are setting a default username and an email for anything related to git on the local machine.
However, you can override these settings in a config file located here:

```bash
project/.git/config
```

By simply editing/appending this file, you can override the global settings for the local project. The config file format is similar to .yml and should look like this:

```yml
[core]
	editor = atom
[user]
	name = bill johnson
	email = work.email@place-of-employment.com
```

By doing this, the global settings are preserved for all other projects, but any pushes from this repo will be overriden by the config file.

