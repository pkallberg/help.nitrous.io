---
layout: article
title: Redis Cloud
published: true
categories: [databases]
---

[Redis Cloud](http://redis-cloud.com/) is a fully-automated cloud service for hosting your Redis dataset.

To get started, sign up with [Redis Cloud](http://redis-cloud.com/). Once signed up, login and click on New Redis Subscription:

![Redis Cloud Subscription](/images/articles/redis-cloud-subscription.png)

From there you will want to select your plan, and specify a resource name and password.

![Redis Cloud Configuration](/images/articles/redis-cloud-configure.png)

Next you will want to select the region which is closest to you.

![Redis Cloud Region](/images/articles/redis-cloud-region.png)

### Setting up the Database configuration (Ruby/Rails)

If you are building a Rails app, follow this step to connect your app to Redis Cloud.

Navigate in your menubar to 'My Resources' > 'Manage', and from there click on your new database. You will be taken to the settings page which will provide you with the host, port, and password needed for your app.

![Redis Cloud Settings](/images/articles/redis-cloud-settings.png)

Grab each of the values and assign them to environment variables in your
"~/.bashrc" file on your Nitrous.IO box. This will ensure that every time you log into your Nitrous.IO box, your
database credentials will be available as environment variables to use
in any of your apps. It is good practice to namespace your environment
variables with the environment that you want to use your database in
(development or test), like so:

![Env Variables](/images/articles/redis-bashrc.png)

If you want the environment variables to be loaded immediately, run:
    source ~/.bashrc

Within your Rails app, update your Gemfile to include the [redis-rb](http://github.com/redis/redis-rb) client:

    gem 'redis'

Next you will want to install the gem via Bundler:

    bundle install

Create a new redis.rb initializer in config/initializers/ and add the following code:

    $redis = Redis.new(:host => ENV['REDIS_CLOUD_HOST'], :port => ENV['REDIS_CLOUD_PORT'], :password => ENV['REDIS_CLOUD_PASSWORD'])