---
layout: article
title: Basic Access Authentication
published: true
categories: [tutorials, rails, django, faq]
---

### Introduction

Basic access authentication (Basic Auth) is supported on all Nitrous boxes by default. Basic Auth is a simple technique which uses static, standard HTTP headers in order to enforce access controls. This will allow you to prompt users for a username and password when making a request.

### Implementation

Basic Auth is supported by default on all Nitrous boxes. You do not need to make any special configurations when [previewing](/preview/) the app.

### Rails Example

Within your Rails 4 app you can add authentication by including the following code in your controller:

    class PostsController < ApplicationController
	   http_basic_authenticate_with name: "foo", password: "bar", except: :index

	   def index
	     render text: "This text can be seen by everyone."
	   end

	   def edit
	     render text: "You can only view this if you know the username and password."
	   end
	end

More documentation can be found at [http://api.rubyonrails.org/classes/ActionController/HttpAuthentication/Basic.html](http://api.rubyonrails.org/classes/ActionController/HttpAuthentication/Basic.html)

### Django Example

Django bundles authentication within djange.contrib.auth.

1. Place `django.contrib.auth` and `django.contrib.contenttypes` within your INSTALLED_APPS setting.

2. Run the following command within the console to create the necessary database tables:

    manage.py syncdb.

>The default settings.py file may already include 'django.contrib.auth' and 'django.contrib.contenttypes' in INSTALLED_APPS already. If your app already has this installed then running `manage.py syncdb` may not be necessary, although it won't hurt to run the command again.

More documentation can be found at [https://docs.djangoproject.com/en/1.1/topics/auth/](https://docs.djangoproject.com/en/1.1/topics/auth/)
