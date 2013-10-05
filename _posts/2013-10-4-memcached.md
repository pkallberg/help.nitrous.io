---
layout: article
title: Setting up Memcached with Autoparts
published: true
categories: [databases]
---

### Prerequisites

* Nitrous.IO box with the package manager Autoparts installed. To ensure Autoparts is installed, run the command `parts` within the terminal. Take a look at the [Autoparts guide](/autoparts/) for installation instructions.

### Install Memcached

You can quickly install Memcached using Autoparts. Within the terminal, run the following command to install:

    parts install memcached

### Connecting to Your Rails App

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


>For information on connecting to an external Memcached database, please view our [MemCachier guide](/memcachier/).