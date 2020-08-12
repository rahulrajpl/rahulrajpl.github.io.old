---
title: Alternative for forticlient vpn tool
date: 2020-08-11 00:00:00 Z
categories:
- network
layout: post
comments: true
---

-----------------------
### Problem Statement
-----------------------
For several days, I have been facing issues with the 'Forticlient' VPN client on my linux machine. With limited knowledge in networking, I was unable to resolve the issues causing the following error

![alt](/static/img/forti/forticlient.png)

![alt](/static/img/forti/err1.png)

![alt](/static/img/forti/err2.png)

-----------------------
### Alternative solution
-----------------------

Solution is to use [openfortivpn](https://github.com/adrienverge/openfortivpn). Following paragraphs explains how to use this tool to setup a VPN.

#### Step 1. Download and install tool

Use the following command to install the tool on Ubuntu/Kubuntu 18.04+

{% highlight bash %}

sudo apt install openfortivpn

{% endhighlight %}

#### Step 2. Initial configuration for VPN

Open `/etc/openfortivpn/config file` and edit the settings as follows

{% highlight bash %}
host = 
port = 
username = 
password = 
{% endhighlight %}

#### Step 3. Connect the VPN

Once the configuration is done, we can start using the tool by following command.

{% highlight bash %}

sudo openfortivpn

{% endhighlight %}

You can use the option '-c' to specify the configuration file for a particular VPN.
Once the connection is ready, you will see a message like below, indicting that the VPN tunnel is up and running

{% highlight bash %}

INFO:   Connected to gateway.
INFO:   Authenticated.
INFO:   Remote gateway has allocated a VPN.
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
INFO:   Got addresses: [<IP>], ns [<IP>, <IP>]
INFO:   negotiation complete
INFO:   Got addresses: [<IP>], ns [<IP>, <IP>]
INFO:   negotiation complete
INFO:   Got addresses: [<IP>], ns [<IP>, <IP>]
INFO:   negotiation complete
INFO:   negotiation complete
local  IP address 10.10.11.227
remote IP address 192.0.2.1
primary   DNS address <IP>
secondary DNS address <IP>
INFO:   Interface ppp0 is UP.
INFO:   Setting new routes...
INFO:   Adding VPN nameservers...
INFO:   Tunnel is up and running.


{% endhighlight %}

