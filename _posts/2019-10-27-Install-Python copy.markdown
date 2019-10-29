---
layout: post
title:  "Install python3.6+ for local user on remote machine without root access"
categories: [python]
comments: true
---

I have recently encountered an issue where I have access to remote server, but the python version installed on it was 3.4. My application required 3.6+ and I do not have root access to install it using apt. So here are the steps I have followed: -

### Installing Python 3.6 (works with any version per say)

1. Get the official download link from python.org website(Example. https://www.python.org/ftp/python/3.6.9/Python-3.6.9.tgz)

2. Download the python source release and get the folder readied for installation from source.

{% highlight YAML %}
$ wget https://www.python.org/ftp/python/3.6.9/Python-3.6.9.tgz
$ tar zxfv Python-3.6.9.tgz
$ find ~/inflated_location/Python-3.6.9/Python -type d | xargs chmod 0755
$ cd Python-3.6.9
{% endhighlight %}

3. Install from source
{% highlight YAML %}
$ ./configure --prefix=~/inflated_location/Python-3.6.9/Python
$ make
$ make install
{% endhighlight %}

4. Export the path variable
{% highlight YAML %}
$ nano ~/.bashrc
$ export PATH=~/inflated_folder/python/Python-3.6.9/:$PATH
$ source ~/.bashrc
{% endhighlight %}

Now you have python3.6 installed for logged in user and can be invoked now using command `python`

### Installing py packages.

The easiest way that I have followed is

{% highlight YAML %}
$ python -m pip install <package-name> --user
{% endhighlight %}

