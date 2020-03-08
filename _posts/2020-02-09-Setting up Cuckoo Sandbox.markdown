---
title: Setting up Cuckoo Sandbox and Kioptrix for security hands-on
date: 2020-02-09 00:00:00 Z
categories:
- security
layout: post
comments: true
---

-----------------------
### Introduction
-----------------------

In this blog, we will see how to set up the cuckoo sandbox and virtual box for malware analysis and installing 'kioptrix' boot-to-root VMs for penetration testing exercise. It is assumed that the host machine is installed with Ubuntu 18.04 or above with VirtualBox software.

-----------------------
### Configuring Cuckoo Sandbox
-----------------------

Step 1: Download Cuckoo_setup.zip from Google Drive(*Link will be provided on request*)

Step 2: "Run cuckoo_framework_install.sh" after unzipping the downloaded file from step 1. Cuckoo will work with python2 at the time of writing this, however, active development for porting the tool to python3 is in progress this year.

Step 3: Step 2 will install a preconfigured Windows operating system to the VirtualBox. A new configuration file will be generated during the installation. Few configuration changes to be done will be after the following step.

Step 4: Open up cuckoo2 in the VM. Check the IP address of the machine by running command 'ipconfig' in the cmd prompt. You will see and IP like **192.168.56.10X**. Now go to the Machine tab, click on 'Take Snapshot' to save a snapshot of the machine.

Step 5: Final configuration changes to be done for cuckoo sandbox is as follows-[^1]

-   Go to the path ‘/home/username/.cuckoo’ and find the ‘conf’ folder.
-   You only need to change three configuration files
namely ‘cuckoo.conf’, ’virtualbox.conf’, and ‘routing.conf’.
-   cuckoo.conf: The fields to be changed in this configuration file are machinery name, resultserver IP, and analysis timeout. The machinery
name is to be VirtualBox, resultserver ip addresss is to be the ip address
of the virtual network interface (vboxnet0), and the analysis timeout is
to be set as 20 seconds instead of 120 seconds.
-   virtualbox.conf: You are using virtualbox as a virtual machine, so you
need to update the configuration details of virtualbox.conf file. This file
contains the information about the network interface. In your case, it is
vboxnet0. The machine name is the same as the virtual machine name.
In your case, you imported the cuckoo2.ova file to virtualbox. Therefore,
your machine name will be cuckoo2. Label field is also same as the
machine name. Cross verify the host machine IP address under 'platform' and 'Cuckoo2' IP address you have checked while taking snapshot. Ensure the snapshot name is also correctly configured in this file.
-   routing.conf: This file contains the information about the routing. To
disable the Internet, set the Internet field as none in this configuration file.
If you want to create some fake Internet services, then set yes in the
inetsim field. If you are using inetsim, then you need to install the debian
package of inetsim into your host machine and change the
DNS_default_IP from the /etc/inetsim/inetsim.conf file. As a beginner,
we discourage you to do this for now. When we consider malware such
as bots, you might have to enable this.

This completes the Cuckoo sandbox setup and is ready or malware analysis. Three main steps are 

- **Cuckoo clean** - this will clean the cuckoo generated reports earlier.(/home/user/.cuckoo/storage/analyses.)
- **Cuckoo submit <file>** this will add task for <file> analysis
- **Cuckoo** - this will initialize the automated malware analysis.




A specifically instrumented Windows 8 Operating System for Malware Analysis is available in the google drive. It includes programs such as Strings, upx packer, peid, resource hacker, DependencyWalker, PEView, Process Explorer, ProcMon, IDA Pro, and pstools. 

**Warning**: The VM should be configured for 'host-only' network or, it may harm the host machine.


-----------------------
### Configuring Kioptrix for Pentesting practice
-----------------------
Step 1: Download Kioptrix level 1 from this [link](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/)

Step 2: You will see a vmdk file when the download finishes. Since we are using virtualbox we need to setup vmdk on virtualbox.

Step 3: Following steps are needed for the linking of vmdk with virtualbox[^2]

- Open VirtualBox and create a new virtual machine, or open an existing one.
- Click the "Settings" button.
- Click "Storage."
- Click "SATA Controller."
- Click "Add Hard Disk."
- Navigate to and double-click on the VDMK file.
- Click "OK" to save the setting.
- Click the green "Start" icon to open the VMDK file and boot the virtual machine.

By default, if you boot the kioptrix from virtualbox, it will most likely end up in a 'kernel panic'. Some more configurations are required before we get to handson with kioptrix boot-to-root VMs. Follows steps:[^3] 

-   Create a new VM and choose not to use a disk
-   In “Settings -> Storage”, remove the SATA controller entirely and under the IDE controller add an new (existing) disk - and select the VMDK.
-   Under “Settings -> Audio” untick “Enable Audio”
-   Under “Settings -> Network” expand “Advanced” and change the Adaptor Type to “PCnet-PCI II (Am79c970A)”
-   Under “Settings -> Ports -> USB” untick “Enable USB Controller”


-----------------------
### References:
-----------------------
[^1]: Prof. Sandeep Shukla  and Mr. Nitesh Kumar (C3i center, IIT Kanpur)
[^2]: https://smallbusiness.chron.com/open-vmdk-virtualbox-28847.html
[^3]: https://www.hypn.za.net/blog/2017/07/15/running-kioptrix-level-1-and-others-in-virtualbox/
