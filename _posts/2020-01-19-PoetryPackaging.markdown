---
title: Packaging and shipping your python tools using Poetry
date: 2020-01-19 00:00:00 Z
categories:
- python
- bash
layout: post
comments: true
---

In this blog let's see how we can package an application and distrubute it using tool called **poetry**.[^3]

-----------------------
### Step 1. Download and Install Poetry
-----------------------

~~~bash
$ curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python
$ source $HOME/.poetry/env
~~~
Check the installation correctly by executing
~~~bash
poetry --version
~~~

If this throws and error regarding 'threads' like the one below

~~~bash
rahul@rahul-lap:~$ poetry --version
/home/rahul/.poetry/lib/poetry/_vendor/py2.7/subprocess32.py:149: RuntimeWarning: The _posixsubprocess module is not being used. Child process reliability may suffer if your program uses threads.
  "program uses threads.", RuntimeWarning)
Poetry version 1.0.2
~~~
, you might need to change the first line in configuration `~/.poetry/bin/poetry` from `#!/usr/bin/env python` to `#!/usr/bin/env python3`. Save this file and execute `poetry --version` again to check for errors if any.

-----------------------
### Step 2. Packaging
-----------------------

If you have a simple script written in python, something similar following 'demo-tool'
~~~python
def main():
	print("Hello World")

if __name__ == '__main__':
	main()
~~~
, you have to go the project directory, open up the terminal and execute, `poetry init`. This command will guide you to create the most important file called `pyproject.toml`, which will orchestrate the packaging for you. Once the interactive generation is finishied, this file will look like below

~~~sh
[tool.poetry]
name = "demo-tool"
version = "0.1.0"
description = "a demo tool for printing hello world"
authors = ["Your Name <you@example.com>"]
license = "MIT"

[tool.poetry.dependencies]
python = "^3.7"

[tool.poetry.dev-dependencies]

[build-system]
requires = ["poetry>=0.12"]
build-backend = "poetry.masonry.api"

~~~
You can add an entry point to the file using 'console_script' in poetry way. Following lines to be appended to our demo program.
~~~bash
[tool.poetry.scripts]
demo-tool = 'demo-tool:main'
~~~
In case your program has some dependecy, you can add it via `poetry add <package-name>`. For example, if your program depends on beautifulsoup webscrapping library, you have to add this dependency to the toml file by running the command `poetry add beautifulsoup4`

-----------------------
### Step 3. Distributing 
-----------------------

Once all your packages are ready to be shipped, you can publish it in PyPI, which is repo of python packages used by the popular tool `pip` [^4]
Run the following command to publish your package

~~~bash
poetry build
~~~

Then publish it(Here you have to enter your pyPI credentials)

~~~bash
peotry publish
~~~

Or you can do it with single command as below

~~~bash
poetry publish --username <YOUR-USERNAME> --password <YOUR-PASSWORD> --build
~~~

If you do not have an account in PyPI, go to [pypi.org](https://pypi.org) and create and account.

Now that your tool is available to outside world to use.

-----------------------
### Step 4. Installation and Usage
-----------------------

Now anyone can install this tool by running,
~~~bash
$ sudo pip3 install demo-tool
~~~
This will create a system-wide availability of the command 'demo-tool' and can be run by simply executing `demo-tool` anywhere from the system.

If you want to locally install it, create a virtual environment using `virtualenv venv` and activate it using `source /venv/bin/activate` and then run `pip install demo-tool`. This will be available locally only to this virtual environment.[^1]

-----------------------
### References:
-----------------------
[^1]: https://packaging.python.org/guides/distributing-packages-using-setuptools/#setup-args
[^2]: https://github.com/python-poetry/poetry
[^3]: https://python-poetry.org/
[^4]: https://pypi.org/
