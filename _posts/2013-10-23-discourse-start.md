---
layout: article
title: Start hacking on discourse in 60 seconds
published: true
categories: [tutorials,rails]
---

[Discourse](https://www.discourse.org) is a powerful, open source forum application built on top of [ruby on rails](https://www.rubyonrails.org) & [ember.js](https://www.emberjs.com).  

After playing around with [some sites](https://discussion.heroku.com/) [already running](http://discuss.howtogeek.com/) the [software](http://bbs.boingboing.net/), I decided to migrate a forum that I host to Discourse. 

## Setting up the Development Environment

Discourse is a robust application with a lot of moving parts.  Vagrant seems like overkill as I don't want to have to install VirtualBox and Vagrant on my machine.  Vagrant is a great tool, but the separate images take up too much space on my SSD and running vagrant takes too long.  

### 1. Create a new box

Discourse runs multiple services and consumes a fair bit of RAM and storage.  I'm going to boot up a box on [Nitrous.IO](https://www.nitrous.io) with 768MB of RAM and 1.5GB of storage to get me started.  Discourse recommends [2 GB of RAM](https://github.com/ajhit406/discourse/blob/master/docs/INSTALL-ubuntu.md) but I'll try this out for development. I can always allocate additional resources later.

![New Box](/images/articles/discourse/new-box.png)

### 2. Fork Discourse

If you want to do any customizing of discourse (why wouldn't you?), you'll want to fork the discourse repo. 

[Click here to Fork Discourse](https://github.com/discourse/discourse/fork)

Once you've forked the repo, you can jump into the Nitrous.IO IDE and clone it to your box. 

![Clone Discourse](/images/articles/discourse/cloned.png)

### 3. Install Dependencies

Next we'll use the Nitrous.IO [Autoparts](http://blog.nitrous.io/2013/09/18/introducing-autoparts-for-nitrous-io.html) package manager to install redis & postgres.  This is as easy as running: 

    parts install redis
    parts start redis

    parts install postgresql
    parts start postgresql

### 4. Configure Rails App

First, we'll need to move into the `discourse` folder and run bundle install: 

    cd workspace/discourse
    bundle install 

This is probably going to be the most time consuming task of the entire post since discourse uses about 10,000 gems.  Of course, we're not complaining…

    cp config/database.yml.development-sample config/database.yml
    cp config/redis.yml.sample config/redis.yml

### 5. Configure Postgres and Install Seed Data

Next, we'll create the development and test databases.  We're going to just keep the legacy `vagrant` user, even though we're not using vagrant.  You can just copy and paste the following commands one-by-one into the terminal on your Nitrous.IO box: 

    createuser --createdb --superuser -Uaction vagrant
    psql -c "ALTER USER vagrant WITH PASSWORD 'password';"
    psql -c "create database discourse_development owner vagrant encoding 'UTF8' TEMPLATE template0;"
    psql -c "create database discourse_test        owner vagrant encoding 'UTF8' TEMPLATE template0;"
    psql -d discourse_development -c "CREATE EXTENSION hstore;"
    psql -d discourse_development -c "CREATE EXTENSION pg_trgm;"

When you're done, load the seed data: 

    psql -d discourse_development < pg_dumps/development-image.sql

Finally, we'll want to load the database migration in rails: 

    bundle exec rake db:migrate db:test:prepare db:seed_fu

### 6. Starting up Discourse

Now we've got our app cloned, gems installed, database created and seed data imported, we're ready to run the app and check out the preview.  In the app's root directory, run: 

    rails s

Then, in the preview menu at the top of the web IDE, click `preview > Port 3000`

![Preview Menu](/images/articles/discourse/preview-menu.png)

And you'll see that we're up and running!  w00t!  

![Discourse Home](/images/articles/discourse/main.png)

(Note that the first time the app loads, it might take anywhere from 10-20 seconds.  This is because discourse has a large amount of client-side code that needs to be downloaded before the app can run)

### 7. Customizing Discourse

This is a fully functional development environment, and you have your own fork of discourse running so you can customize it as you please, then merge upstream changes as the discourse team continues to improve the system. 

Let's go ahead and kill those rounded corners on the tables, they're so not web flat.0: 

Change line 43 of `app/assets/stylesheets/desktop/topic-list.scss`: 

    @include border-radius-all(0 0 0 0);

Line 85:  

    @include border-radius-all(0 0 0 0);
 
Line 88: 

    @include border-radius-all(0 0 0 0);
    
And we have square corners on all the topic lists.  Very web 3.0, if I don't say so myself...

![Sharp edges](/images/articles/discourse/new-icon.png)

That was easy.  Stay tuned to [@nitrousio](https://www.twitter.com/nitrousio), we've got an even easier way to install discourse that is going to blow your mind.  
