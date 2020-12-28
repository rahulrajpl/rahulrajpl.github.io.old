---
title: Install Python modules to machine without internet
date: 2020-12-26 00:00:00 Z
categories:
- python
layout: post
comments: true
---


Often times, a python application is deployed on a machine with internet connectivity. In such cases, settingup the environment in respect of the dependecies would be fairly easy, as the packages or modules are installed using the regular `pip` or `conda` commands. The problem comes when the machine to be deployed is not internet facing. Following steps are to be taken in such scenarios (using pip)

-----------------------
#### Step 1. Download required packages/modules

First you will have to download the modules using an internet facing machine and locally store them in a repository. Use the following command to download the requisite dependecies

{% highlight python %}

pip download -d <download-folder> <package-name>

{% endhighlight %}

-----------------------
#### Step 2. Generate a requirements.txt file using pip

You can create a requirements.txt file using the following command

{% highlight python %}
pip freeze > requirements.txt
{% endhighlight %}

-----------------------
#### Step 3. Deploy the app on non-internet facing machine 

Move the Folder in which the dependencies are downloaded along with the requirements.txt file

-----------------------
#### Step 4. Install dependecies locally using the following command

Following commands will install the dependecies which are downloaded earlier on the development PC.

{% highlight python %}
pip install --no-index -f <packages-folder> -r requirements.txt
{% endhighlight %}




