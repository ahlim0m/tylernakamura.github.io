---
layout: post
title: "The Hello World of OpenStack"
date: 2016-06-07 09:30
comments: false
categories: Openstack beginner basic tutorial guide tut
---

**Note: This post is currently unfinished...**

### Openstack Devgroup VM Stuff
upon sshing into vagrant box, source the stackrc file:
```bash
source /vagrant/stackrc
```

### Creating an Image
**Create an image from an iso:**
```bash
openstack image create --file <path to iso image> <name of image>
```
ie:
```bash
openstack image create --file /vagrant/ubuntu-16.04-server-amd64.iso ubuntu-server-image
```

### Creating a Server
**Create a server from an image:**
```bash
openstack server create --image <image> --flavor <flavor> <server name>
```
ie:
```bash
openstack server create --image my-cirros-image --flavor m1.tiny my-cirros-server
```

**Display available flavors:**
```bash
openstack flavor list
```

If the creation was successful, the server will show in the server list:
```bash
openstack server list
```

### Security Groups
We are now looking to make our newly made server accessible via ssh and/or ping. 
The default security group assigned to this server, is sometimes not allowed access to ssh and/or ping. 
This sections aims to first create a new security group, create rules that allow for ping and ssh:

**Show a list of your current security groups:**
```bash
openstack security group list
```

**Create a new security group:**
```bash
openstack security group create <name of group>
```
ie:
```bash
openstack security group create my-ssh-group
```
Rules then need to be added a to a given security group. 

**Show rules for a given security group:**
```bash
openstack security group show <name of group>
```
ie:
```bash
openstack security group show my-ssh-group
```
Now that we have a new security group, we can begin adding rules to it that will allow ssh and ping.

**Add rule to a security group:**
```bash
openstack security group rule create <group> --protocol <protocol> --dst-port <port-range>
```

**Allow ssh to port 22:**
```bash
openstack security group rule create my-ssh-group --protocol tcp --dst-port 22:22
```

**Allow pings to all ports:**
```bash
openstack security group rule create my-ssh-group --protocol icmp --dst-port -1:-1
```

It may be prudent to remove your server from the default security group.
The default security group may have stricter rules and will essentially override the newly created security group.

**Remove a given server from a given security group:**
```bash
openstack server remove security group <server> <group>
```
ie:
```bash
openstack server remove security group my-ssh-server default-security-group
```

