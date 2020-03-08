---
title: Passive OSINT tools for beginners
date: 2020-01-22 00:00:00 Z
categories:
- security
layout: post
comments: true
---

-----------------------
### Introduction
-----------------------

Let's see some of the most popular ways an entry-level OSINT wiz gets to do the passive reconnaissance of targeted computers and network. It's passive' as we do not directly engage with the target resources. 

A summary of techniques/tools, before jump into the details, are as follows: - [^1]
- Target Validation using Whois, nslookup, dnsrecon
- Finding Subdomains using Google Fu, dig, nmap, sublis3r, bluto, crt.sh, etc.
- Fingerprinting using nmap wappalyzer, whatweb, biltwith, netcat
- Data Breaches using haveibeenpwned and similar lists

**Google Hack**

Google hack is nothing but a clever google search, exploiting the search parameters to specifically target and get the results. Techniques are openly available on many websites and can be easily accessed. The website I follow personally is https://www.exploit-db.com/google-hacking-database. This compiles various working keywords you can search, for eg. "passwords.xlsx" ext:xlsx will fetch the password file from websites.

**Shodan - the hackers search enginer**[^2]

Go to the website shodan.io This requires you to register for an account to be able to search and use the filter. Eg search for 'cisco and router' and press search, it pull up IP add and devices. To filter country wise, there are filters available to refine the search for a target resource. A great tool for a passive OSINTer

**Breach Data**

There are millions of breached usernames and passwords in cleartext available all around the internet. Grab them at checking them is also another big way to find the potential target.

**hunter.io**

This is another favorite place for hackers to gather intelligence. Explore the website to find out more. 

**theHarvester**

This tool is available in Kali Linux. Following is how this tool can be useful.

~~~
theHarvester -d tesla.com -l 500 -b google
~~~

**haveibeenpwned**

Go to this website haveibeenpwned.com, and see a particular email id is compromised or not. This is a great tool to check breached data as well.

**DNS Recon**

A tool call bruto can be used for DNS recon. This tool is open-sourced and is available in the GitHub repo [here](https://github.com/darryllane/Bluto)

**Skiptracer**

This is another OSINT scraping framework. This is available in the GitHub repo [here](https://github.com/xillwillx/skiptracer)

**crt.sh**

Go to the website and search for a company website and it will pull out all the subdomain registered with the parent domain and with few other details

**Technology behind a website**

Tools like 'wappalyzer' and '[builtwith](https://builtwith.com/) can be used to find the technologies used in a particular website, specifically to check the version of the tools and see if that version has any exploitable vulnerabilities. Both these tools have browser extensions available, which makes the job easier.

**Whatweb**

This is another command-line tool available in Kali Linux. The usage of the tool is as follows: -

~~~
whatweb -v tesla.com
~~~

Data pulled by this tool is similar to what wappalyzer and builtwith can do.

**Netizenship**

This is a tool I wrote to find out if a given username is already registered with popular websites or not. Project is open-sourced [here](https://github.com/rahulrajpl/netizenship)

-----------------------
### References:
-----------------------
[^1]: Ethical Hacking course by @thecybermentor
[^2]: Penetration Testing and Ethical Hacking course by *Cybrary*
