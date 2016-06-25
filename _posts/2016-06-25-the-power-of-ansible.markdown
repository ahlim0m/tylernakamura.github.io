---
layout: post
title: "The Power of Ansible"
date: 2016-06-25 16:03
comments: false
categories: Ansible orchestration devops
---

Imagine you own more than 10 servers. 
Some of your computers are purposed as databases, others are compute nodes and others are web servers.
Now trying to envision managing such a cluster.
Without other tools, in order to roll out changes or add in additional machines it would require a great deal of manual configuration.
Effectively automating the process of configuring groups of machines (virtual or real) is what Ansible aims to accomplish.
With Ansible, it is possible to define an inventory and group machines into them.
Ansible can be seen as a direct competitor to other tools such as Chef and Puppet.
For example, an inventory might look something like this:

```
[web servers]
www.healthynuggets.com
www.puppiesunited.net

[compute nodes]
192.168.1.2
192.175.2.3

[databases]
db1.health.com
db2.pup.com

# note that you can define a range of servers
[sample-range of servers]
192.168.1.[45-100]

```

<img src="/images/ansible-logo-transparent-background.png"/>

Now that you have all of your machines organized in such a way, rolling out targeted changes is easier than ever.

Ansible also features what are called "playbooks."
Playbooks are used to automate the process of configuring a remote machine.
Because the way in which you configure the machine is stored in a file, the process is repeatable, easy to debug, and easy to repeat.
It may be possible to achieve this with custom scripts, but the process is greatly simplified due to a very human readable language that Ansible utilizes to create these playbooks.
To increase granularity and preserve a modicum of object orientation, Ansible uses roles and tasks.
A task might look something like this:

```
---
# possibly saved as tasks/foo.yml

- name: placeholder foo
  command: /bin/foo

- name: placeholder bar
  command: /bin/bar
```

A playbook contains an array of these tasks.

With ansible, it is possible to run a single command on a cluster of servers.
With this power, you can only imagine what is possible.
Here is a sample command being run to the [database] group, using the user bob, with the module ping:

```
ansible database -m ping -u bob
```

With this, all machines in the "database" group, from the user bob, will use the module ping and return the output to the host machine.
This is a simple example, but it serves to show you how easy it is to run a single command on a group of machines.

It is also worthy of mentioning that Ansible is agentless.
In other words, it doeesn't require the target servers to be running an agent, or daemon.
Instead it simply utilizes ssh, which in many cases can be more convenient when working with a brand new server.
It does however also require Python, which isn't too much to ask for these days.

With the advancement of virtualization technology, groups of clean disposable VMs continue to grow both in popularity and in size.
Utilizing tools like Ansible serves as a very powerful to begin to manage this growing cloud.

