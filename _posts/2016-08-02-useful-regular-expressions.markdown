---
layout: post
title: "Useful Regular Expressions"
date: 2016-08-02 13:49
comments: false
categories: Regex useful
---

Just saving some RegEx that I use :D

### Season and Episode:
```bash
[Ss]\d{2}[Ee]\d{2}
```
Example:

- S01E10
- s11E12
- S30e01

### Video Types
```bash
\.(mkv|mp4|avi|mov)
```
Example:

- mkv
- mp4
- avi


### ipv4 address
```bash
^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}↵
(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$
```
[source](https://www.safaribooksonline.com/library/view/regular-expressions-cookbook/9780596802837/ch07s16.html)

## Cheat Sheets:

- [cheatography.com](https://www.cheatography.com/davechild/cheat-sheets/regular-expressions/)
