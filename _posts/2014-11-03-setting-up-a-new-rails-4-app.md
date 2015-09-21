---
layout: post
title: "Setting Up a New Rails 4 App"
modified:
categories:
excerpt: "A quick setup guide to setting up a new Rails 4 app."
tags: []
comments: true
image:
  feature: ralphwilson.jpg
date: 2014-11-03T18:45:18-06:00
---
## Create the new rails app:

	{% highlight ruby %}
	rails new <directory> -T -d postgresql
	{% endhighlight %}

## Edit the Gemfile:

Remove the <code>gem turbolinks</code>. You can also get rid of <code>sdoc</code>, <code>jbuilder</code>, and <code>coffee-rails</code>. Add the following gems:

	{% highlight ruby %}
	gem 'activeadmin', github: 'activeadmin'
	gem "devise"
	gem 'simple_form'
	gem 'browser-timezone-rails'

	group :development do
	  gem "better_errors"
	  gem "quiet_assets"
	end

	group :development, :test do
	  gem "capybara"
	  gem "capybara-screenshot"
	  gem "database_cleaner"
	  gem "factory_girl_rails"
	  gem "faker"
	  gem "poltergeist"
	  gem "pry-nav"
	  gem "pry-rails"
	  gem "pry-stack_explorer"
	  gem "pry-theme"
	  gem "rspec-rails"
	  gem "rubocop", require: false
	  gem "shoulda-matchers"
	  gem "spring-commands-rspec"
	end
	{% endhighlight %}

## Bundle install
## Generate some files:

	{% highlight ruby %}
	rails generate rspec:install
	rails generate simple_form:install
	rails generate active_admin:install //skip this one if you arent using active admin, maybe devise install instead
	spring binstub --all
	rake db:create db:migrate
	{% endhighlight %}

## Try rake or rspec and make sure warning are disabled in Rspec.
