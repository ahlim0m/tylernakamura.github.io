---
layout: post
title: "Why I am Getting Started with Docker"
date: 2016-07-24 21:20
comments: false
categories: Docker getting started
---

Docker is an open source containerization platform that seems to have a very promising future.
Docker aims to ease the process of shipping applications easily.
If you are familiar with the Vagrant tool, docker is similar but it is purposed for production environments and not development environments.
The traditional way of shipping applications is to ship an entire virtual machine.
However, this proves to be far meatier than what is actually needed.
A docker container is lighter than an entire VM but it still satisfies all neccesary dependencies.


Looking at the google trend for the keyword "docker," you can see that its popularity speaks for itself:

<img src="/images/docker-trend.png"/>

After learning some basic server administration, I have since deployed a few servers on static IPs of my own across the globe.
I have been continuing to write software/applications on my local machine, but I want them to be deployed to my servers for public use.
The power of Docker allows me to ship my software quickly to all my desired servers and ensure that all of the dependencies are met.
This is because, I can ensure that everything works properly in the container on my local machine before actually shipping the product.

Another reason why I have been spending time with Docker, is the fact that containers are so much more lightweight than a standard VM.
In fact, just looking at the resources being used on my machine will show that a container really only uses what it absolutely has to.
This is unlike a traditional VM that seems to always hog a fixed (or more) amount of resources.
Running a multi-compute node cloud set up will have my computer sounding like it is about to take off!
This doesn't mean that VMs are completely useless at this point, it just means that yet another actor has entered the stage of software development.

On top of all of this, the project is open source and has a great deal of community involvement.
If you are looking to deploy your application, it would be a mistake to overlook Docker as an option.
