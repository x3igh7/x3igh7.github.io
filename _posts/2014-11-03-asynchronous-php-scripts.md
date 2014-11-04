---
layout: post
title: "Asynchronous PHP Scripts"
modified:
categories:
excerpt: "How to unblock your php session."
tags: []
comments: true
image:
  feature: ralphwilson.jpg
date: 2014-11-03T19:04:53-06:00
---
At Outsell we've been writing a lot of code that heavily relies on AJAX calls to PHP scripts. Only recently we ran into a problem with this method. To build a UI to handle and track some of our exisiting backend processes, we needed to run a rather heavy MySQL stored procedure that can take a while to run (anywhere from 1 minute to an hour depending on how many records we need to process).

In addition to the AJAX call that initiates the stored procedure, we also had another AJAX call that runs at regular intervals that retrieves progress updates for running processes. As such, the updates were being blocked by the PHP session, which only allows one PHP script to be running at once. We needed a way to get around this since we want to retrieve progress updates for the newly created process. We also may want to perform additional tasks within the UI.

This is where the handy PHP function <code>session_write_close()</code> came into use. We simply plugged this in the start of the PHP function that initiated the process creation through and AJAX call. Such that

{% highlight php %}
public function startProcess($args){
	session_write_close();

	// other code

	return true;
}
{% endhighlight %}

Now the stored procedure process runs in the background without interfering with additional AJAX calls.

Note that if you're doing any work with the PHP session, you will not be able to write to it after invoking this function. However, you will still be able to read from it.
