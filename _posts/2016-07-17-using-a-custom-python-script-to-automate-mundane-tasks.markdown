---
layout: post
title: "Using a Custom Python Script to Automate Mundane Tasks"
date: 2016-07-17 21:19
comments: false
categories: python automate bash
---

Computer automation was the entire reason I first became interested in programming in the first place.
The idea that you could make a computer perform a task for you, for any period of time was fascinating.
My goal in programming is to make a computer do as many of my tasks for me as possible.
Often times, in my work-flow, I will do the same task multiple times.
This is an indication that this task needs to be automated or at least expedited.
Using cron jobs and various APIs, you can nearly automate any task.

In this tutorial, I am going to give an example of a simple chore and show I use a script to expedite the process.
The first step is to first identify the problem.

### The Problem
I strongly prefer that my file names do not contain spaces.
Instead, I prefer dashes as a delimiter.
I also don't like when file names contain capital letters.
By abiding by these rules, I believe that it is easy to sort files, and type file names via the terminal.
These are my preferences and nearly all of my files/directories abide by these rules.
It also seems that all the ***pro*** git-hub repos abide by these rules.
In order to get my files to looks like this, I would often have to type in the old file name and type in the new file name, like so:

```bash
$ mv "OLD FILE NAME" new-file-name
```

Sometimes when I download a new file, the newly downloaded file does not abide by my rules.
Renaming each of the files one by one can be very cumbersome; especially if there were many new files.

### The Solution
The rules that I created for myself are fairly easy to define programmatically.
Renaming a file a file in python might look something like this:

```python
#!/usr/bin/python

def proper_name(file_name):
    file_name = file_name.lower()
    file_name = file_name.replace(' ', '-')
    return file_name

def main():
    import argparse
    import subprocess
    parser = argparse.ArgumentParser()
    parser.add_argument("target", help="the file to be renamed")
    args = parser.parse_args()
    subprocess.call(["mv", args.target, proper_name(args.target)])

if __name__ == "__main__":
    main()
```

With this simple python program, you can easily pass in a file name, and python will construct the new name and rename it.
The usage looks like this:

```bash
$ python rename.py <filename>
```

This is a simple example of how a python program can be used to solve this mundane task.

### Going Further
Automation can be as extreme as you would like it to be.
The great part of programming is that you can decide how automatic you want the process to be.
For myself, I didn't want to have to directly reference the python script every time.
To fix this, I created a hard link to the script in my /usr/local/bin:

```bash
$ ln rename.py /usr/local/bin/bettertitle
```

I then ensured that /usr/local/bin/ was in my PATH variable:

```bash
$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:
```

By doing this, anywhere on my system, I can now just run the command to reference the python script:

```bash
$ ls
BAD FILE NAME
$ bettertitle BAD\ FILE\ NAME
$ ls
bad-file-name
```

Automation can be taken even further if you somehow worked in Cron jobs, and new file detection.
It is entirely up to you how automatic the process should be.

### Conclusion
The purpose of computers are to do hard work so you don't have to.
Don't forget to automate this process.
Let humans do the important work, and use python scripts as a form of automation!
















 
