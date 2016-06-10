---
layout: post
title: "The Hello World of OpenStack"
date: 2016-06-07 09:30
comments: false
categories: Openstack beginner basic tutorial guide tut vagrant devstack trusty64
---

This post outlines the steps required to start an OpenStack Environment using an Ubuntu VM then deploy a server within OpenStack.
The process below will be executed from a Mac OS based machine, but the steps should be highly similar for any other host OS.

**Tools Used:**

- [Vagrant](https://www.vagrantup.com/)
- [Devstack](https://github.com/openstack-dev/devstack)
- [OpenStack](https://github.com/openstack/openstack)
- [Virtual Box](https://www.virtualbox.org/)
- [Git](https://git-scm.com/)

### Using Vagrant to create a clean development environment
DevStack recommends for good reason, recommends using a VM to stand up an OpenStack development environment:

```
 We strongly recommend that you run stack.sh in a clean and disposable vm when you are first getting started.
```
[-source](https://github.com/openstack-dev/devstack)

Use the [installation guide for Vagrant](https://www.vagrantup.com/docs/installation/) for your machine, then follow the [getting started guide ](https://www.vagrantup.com/docs/getting-started/index.html) to get a VM running.

Note that Vagrant requires Virtual Box in order to run as it essentially wraps the [VBoxManage API](https://www.virtualbox.org/manual/ch08.html).

I used Ubuntu Trusty64 as my OS, DevStack at this is time is being developed for Ubuntu or Fedora.
There were definitely issues with Ubuntu 12.x and DevStack, so I would recommend using 14.x.

Here are the steps after a Vagrant Installation:

```bash
#make a directory for the environment
mkdir my-vagrant-env
cd my-vagrant-env

#initialize and start the machine
vagrant init ubuntu/trusty64
vagrant up --provider virtualbox
```

I learned the hard way that OpenStack needs more memory than what VirtualBox gave it at creation.
Use the API to give it more memory:

```bash
VBoxManage modifyvm <name-of-vm> --memory <amount of memory in mb>
```

You can see what VM's you have running in your current directory by checking the status:

```bash
vagrant status
```

I called:

```bash
VBoxManage modifyvm default --memory 4096
```

At this point, you can ssh into the machine:

```bash
vagrant ssh
```

Congratulations, you now have a nice "clean and disposable vm" for your OpenStack!

Next, we want to install OpenStack using DevStack.
DevStack, is really just a series of scripts that assists in deploying OpenStack.
At this point, lets clone the DevStack repository in our Ubuntu VM:

```bash
git clone https://github.com/openstack-dev/devstack
cd devstack
```

Per the documentation, here are the steps required to stand up OpenStack using DevStack:

```bash
. openrc
./stack
```

If something goes awry during the stack process, be sure to ```./unstack.sh``` before calling ```./stack.sh``` again.

At this point, OpenStack should now be running, the following steps should be focused on deploying an instance.

### Creating an Image

Before we can create a server, we have to create an image based on an ISO.
My OpenStack deployment came with an CirrOS image already installed.
[CirrOS](https://launchpad.net/cirros) is a tiny OS that specializes in running on a cloud.
If you don't have a image already in OpenStack, you can create an image with an ISO as outlined below.
My favorite feature about Vagrant is how easily you can move files into your VM.

To move an ISO into your VM (even while it is running), simply move the file on your host machine into the directory of your vagrant environment:

```bash
mv /path/to/dankfile.awesome /path/to/mv-vagrant-env
```

With this, ```dankfile.awesome``` now exists within the vm at ```/vagrant/```.

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
