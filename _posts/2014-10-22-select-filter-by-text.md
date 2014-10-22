---
layout: post
title: "Select Filter By Text"
modified: 2014-10-22
categories:
excerpt: "A small jQuery plugin that filters select elements."
tags: []
comments: true
image:
  feature: ralphwilson.jpg
date: 2014-10-22T21:19:04-05:00
---
I pulled together some code for a little jQuery plugin that turns a text input field into search field that filters the options in a HTML select. I found that other plugins that purported to do this could not handle larger datasets. By implementing some small improvements such as using .html() once, as opposed to using .append() for each option, as well as including a timeout while typing before the filtering begins - I was able to achieve much better performance.

[Check it out on GitHub.](https://github.com/x3igh7/select_filter_by_text)




