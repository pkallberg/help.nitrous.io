---
layout: article
title: MemCachier
published: true
categories: [databases]
---

### Creating a Cache at MemCachier

MemCachier manages and scales clusters of memcache servers so you can focus on your app.

To get started, signup with [MemCachier](http://memcachier.com/).

[Create a new cache](https://www.memcachier.com/caches/new) and select an EC2 instance, a pricing plan of your choice, and a region. This region should be close to the region of your Nitrous box to ensure a low latency.

![Creating a New Cache](/images/articles/memcachier-ec2-config.png)

Once the cache has been created, you will be provided with the cache's credentials.

![Cache Configuration](/images/articles/memcachier-config.png)

Grab the server, username, and password, and assign them to environment variables in your `~/.bashrc` file on your Nitrous.IO box. 

It is good practice to namespace your environment variables variables with the environment that you want to use your database in (development or test), like so:

![Env Variables](/images/articles/memcachier-env-variables.png)

If you want the environment variables to be loaded immediately, run:

    $ source ~/.bashrc

You can verify that your MemCachier credentials are loaded correctly by
running:

    $ echo $MEMCACHIER_SERVERS

### Connecting to Your Rails App

>To learn how to connect with apps other than Rails, please visit MemCachier's [documentation](https://www.memcachier.com/documentation).

Start by adding the dalli gem to your Gemfile.

    gem 'dalli'

Then bundle install:

    $ bundle install

`Dalli` is a Ruby memcache client. Once it is installed you’ll want to configure the Rails cache_store appropriately. Modify `config/environments/production.rb` with the following:

    config.cache_store = :dalli_store, <MEMCACHIER_SERVERS>.split(","),
                        {:username => <MEMCACHIER_USERNAME>,
                         :password => <MEMCACHIER_PASSWORD>}

The values for `<MEMCACHIER_SERVERS>`, `<MEMCACHIER_USERNAME>`, and `<MEMCACHIER_PASSWORD>` should have been added to your `~/.bashrc` file in the last step.

>In your development environment, Rails.cache defaults to a simple in-memory store and so it doesn’t require a running memcached.

From here you can use the following code examples to use the cache in your Rails app:

    Rails.cache.write("foo", "bar")
    puts Rails.cache.read("foo")

MemCachier has built a small Rails example here: [MemCachier Rails sample app](https://github.com/memcachier/examples-rails).
