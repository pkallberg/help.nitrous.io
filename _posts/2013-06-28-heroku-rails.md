---
layout: article
title: Deploying to Heroku
published: true
categories: [deployment]
---

These instructions will help you deploy your [Rails 3.2](http://guides.rubyonrails.org/3_2_release_notes.html) application to [Heroku](https://heroku.com).

### Things you should know

* Ruby/Rails basic concepts. Your Nitrous.IO box will come preinstalled with Rails 3.2 and Ruby 1.9.2.
* Basic knowledge of Rubygems, [Bundler](http://gembundler.com/).
* Basic knowledge of [Git](http://git-scm.com/).

### Prerequisites

* An [Nitrous.IO Account](https://www.nitrous.io)
* A [Heroku Account](https://www.heroku.com)
* A [Ruby on Rails box](/box-new) on Nitrous.IO

### Authenticate your Heroku Account

All boxes on Nitrous.IO come pre-installed with the [Heroku Toolbelt](https://toolbelt.heroku.com/). So let's go ahead and login to your Heroku Account:

    $ heroku login
    Enter your Heroku credentials.
    Email: aj@domain.com
    Password:

<p class="alert">If you aren't prompted to upload your SSH key or you decide not to upload it now, you'll need to upload it manually.</p>

Since we already generate your public SSH keys on your Nitrous.IO box, you just need to run:

    $ heroku keys:add ~/.ssh/id_rsa.pub

### Create an application

If you're importing an existing application, you can [connect your Github account](/github-add-key) to easily clone projects. For this example, let's create a simple hello application:

    $ rails new hello-app --database=postgresql
    $ cd hello-app

####Database Support####

Nitrous.IO boxes come with Sqlite3 support by default. However, for more complex applications, you might want to use Postgres, MySQL, MongoDB, etc…

<p class="note">Heroku highly recommends using PostgreSQL during development to maintain parity between development and production environments.</p>

Since we're deploying the application to Heroku, let's use Postgres.

Appending the **--database** flag when creating the app will create the appropriate postgres variables in database.yml and will include the pg gem in your Gemfile.

Next, we need to create a development database on [Heroku Postgres](https://postgres.heroku.com). This way you don't need to install Postgres and worry about any issues between your development database and production database. Follow the steps from [this article](/postgres).

### Setup Git

Since we use git to package and push your application to Heroku, lets go ahead and setup git for this application:

    $ git init
    $ git add .
    $ git commit -m "initializing git"

### Deploy to Heroku

First, you'll need to create the app namespace and initialize the app on heroku:

    $ heroku create
    Creating vast-brushlands-7106... done, stack is cedar
    http://vast-brushlands-7106.herokuapp.com git@heroku.com:vast-brushlands-7106.git

Then deploy your code:

    $ git push heroku master
    Counting objects: 63, done.
    Compressing objects: 100% (49/49), done.
    Writing objects: 100% (63/63), 26.35 KiB, done.
    Total 63 (delta 2), reused 0 (delta 0)
    -----> Ruby/Rails app detected
    -----> Installing dependencies using Bundler version 1.3.0.pre.5
    Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin --deployment
    Fetching gem metadata from https://rubygems.org/.....
    Installing builder (3.0.4)
    Installing activemodel (3.2.11)
    Installing rails (3.2.11)
    Your bundle is complete! It was installed into ./vendor/bundle
    -----> Writing config/database.yml to read from DATABASE_URL
    -----> Preparing app for Rails asset pipeline
    Running: rake assets:precompile
    Asset precompilation completed (15.19s)
    -----> Discovering process types
    -----> Compiled slug size: 9.0MB
    -----> Launching... done, v6
    http://vast-brushlands-7106.herokuapp.com deployed to Heroku
    To git@heroku.com:vast-brushlands-7106.git
    * [new branch]      master -> master

Congratulations -- You've deployed your application to Heroku. We encourage you to read up on [Heroku's documentation](https://devcenter.heroku.com/) to handle resource scaling, check processes, logs, etc…