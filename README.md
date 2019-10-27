## Personal Website theme
-------------------------
![Tweet](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2Frahulrajpl%2Frahulrajpl.github.io)

![MIT Licensed](https://img.shields.io/github/license/rahulrajpl/rahulrajpl.github.io?style=social)

This project is forked and customized on top of:-

* [https://agusmakmun.github.io](https://agusmakmun.github.io)
* [A simple grey theme for Jekyll](https://github.com/liamsymonds/simplygrey-jekyll)
* [Super Search](https://github.com/chinchang/super-search)

#### Features

* Sitemap and XML Feed
* Pagination in homepage
* Posts under category
* Realtime Search Posts _(title & description)_ by query.
* Related Posts
* Highlight pre
* Next & Previous Post
* Disqus comment
* Projects page & Detail Project page
* Share on social media
* Google analytics
* HTML Minify _(Compress HTML)_ using [Jekyll Compress HTML](https://github.com/penibelst/jekyll-compress-html)


### Install & Configuration

1. Fork this repository
2. Edit site settings inside file of `_config.yml`
3. Edit your projects at file of `projects.md`, `_data/projects.json` and inside path of `_project/` _(for detail project)_.
4. Edit about yourself inside file of `about.md`

### How to Use?

**a. Add new Category**

All categories saved inside path of `category/`, you can see the existed categories.

**b. Add new Posts**

* All posts bassed on markdown syntax. Allowed extensions is `*.markdown` or `*.md`.
* This files can found at `_posts/`.
* and file name format is `<date:%Y-%m-%d>-<slug>.<extension>`, for example:

```
2013-09-23-welcome-to-jekyll.md

# or

2013-09-23-welcome-to-jekyll.markdown
```

Content of the file be like,

```
---
layout: post                          # (require) default post layout
title: "Your Title"                   # (require) a string title
date: 2016-04-20 19:51:02 +0700       # (require) a post date
categories: [python, django]          # (custom) some categories, but makesure these categories already exists inside path of `category/`
tags: [foo, bar]                      # (custom) tags only for meta `property="article:tag"`
image: Broadcast_Mail.png             # (custom) image only for meta `property="og:image"`, save your image inside path of `static/img/_posts`
---

# your content post with markdown syntax goes here...
```


#### Installing in your local

Follow instruction at official jekyll page to get the local machine for ruby development. Then run the following commands in the cloned directory

```
bundle
bundle exec jekyll build
bundle exec jekyll serve
```

### Contributing

Feel free to [open a bug](https://github.com/rahulrajpl/rahulrajpl.github.io/issues) or [contribute to code](https://github.com/rahulrajpl/rahulrajpl.github.io/pulls)!

### Credits

* Original Theme: [Agus Makmun](https://agusmakmun.github.io)
* Customized by: [Rahul Raj](http://randomwalk.in)