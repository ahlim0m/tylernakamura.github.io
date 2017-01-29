---
layout: post
title: "From Java to Python"
date: 2016-07-10 22:14
comments: false
categories: Java python Python
---

For many years I used Java as my primary programming language.
For various reasons, I now find myself using Python as my primary language.
I wanted to highlight some of the biggest differences for me between the two languages.
Note that these highlights are based on personal experiences.

## Pros of Python

### I love the Python projects
This is most likely to be the most subjective point here:
To really get a sense of what is happening in the open source community, sometimes I will browse [github.com/trending](https://github.com/trending).
In doing this, I can see what projects/authors are trending in the last 24 hours or in the last month.
As a result, I find some interesting projects that I would have never found elsewhere.
You can also sort these projects by language, allowing you to browse just Java, C, Python projects and so forth.
Looking at the Python projects is always my favorite, there always seems to be a different vibe with each language.
I have found that many of the Python projects involve web scraping, web spiders, or networking.
These are topics I always find interesting, so sorting by Python projects always yields fascinating results for me.

### Python is a hackers language
Because of the libraries and the fact that Python is a rather high level language, many security professionals have chosen Python as their language.
This means that much of the cyber security scripts are written in Python.
These can include anything from IDS to pen-testing.
If you are interested in cyber security, Python is definitely worth looking into.

### Pythons blazing development speed
It was weird at first not adding a semicolon at the end of every line.
It was also weird not adding brackets to enclose scope.
But after getting used to these differences, I realized that these were things that only slowed me down.
Python is built with scientists and non-techies in mind, as a result, it often appears to be very human readable.
Pep8 (a Python coding style standard) encourages readability as a core element of the code.
In Python, unlike Java, you are not required to declare classes.
Something as simple as a print statement even is significantly easier to write than in Java:

***Java***
```Java
System.out.println("Hello World");
```

***Python***
```python
print "Hello World"
```

Python is easy to read and write, and it is awesome.

## Cons of Python

### Python is slower than Java
Python is not really known for its significant runtime speed.
From various sources I have read, it would seem that Java runs faster at runtime.
However, I have yet to write something that requires significant low-latency and speed.
For that reason, I have yet to notice the speed difference myself. 

### There are two Python languages
The Python community seems to be divided into two, and it can sometimes be a pain to switch between 2 and 3.
It doesn't seem that this dichotomy has a near end, as there are many projects are fully dependent on Python2.
At the same time, there are some who are adamant about switching everything to Python3.
Whenever this discussion arises, this XKCD always comes to mind:

<img src="/images/xkcd-standards.png"/>

## Conclusion
This is list is far from exhaustive, but these are the main points that come to mind.
In the future, I would mention the Python documentation/community, as it has proven to be fantastic in my experience.
If you haven't looked into Python yet, I certainly recommend giving it a test drive.
