---
layout: article
title: Creating a  Rails app with Amazon RDS
published: true
categories: [integrations, databases]
---

With [Amazon RDS](http://aws.amazon.com/rds/) you can quickly and easily provision and maintain a MySQL, Oracle, or Microsoft SQL Server instance in the cloud.
Lets go over how to get started with a Rails app using the Amazon RDS MySQL engine.

### Prerequisites

Before we get started, make sure you have the following:

* An [Amazon Web Services Account](http://aws.amazon.com/)
* An [Nitrous.IO account](https://nitrous.io)

### Adding a Security Group with Amazon RDS

Lets add the Nitrous.IO box to the Amazon RDS security group. Since This EC2 box will be running in the same region as the Amazon RDS (US West) we can add the internal IP into the Security Group.

Ping your Rails box URI within the Nitrous.IO console to find the internal IP:

    $ ping rails-box-3921.usw1.actionbox.io
    PING ec2-184-169-182-155.us-west-1.compute.amazonaws.com (10.168.125.111) 56(84) bytes of data.
    64 bytes from ip-10-168-125-111.us-west-1.compute.internal (10.168.125.111): icmp_req=1 ttl=64 time=0.130 ms

Login to your [Amazon RDS Console](https://console.aws.amazon.com/rds/home), navigate to Security Groups and create a new security group using the internal IP as a CIDR/IP connection type.

![Security Group Details](https://raw.github.com/action-io/action-assets/master/support/screenshots/amazon_rds_security_group.png)

###  Setting Up a New Instance with Amazon RDS

Within your [Amazon RDS Console](https://console.aws.amazon.com/rds/home) you will want to navigate to Instances and Launch a new DB Instance. When prompted, select the MySQL Database Engine.

When setting up the database remember to select the Security Group you have just created.

![Amazon RDS Settings](https://raw.github.com/action-io/action-assets/master/support/screenshots/amazon_instance_setting.png)

### Create a Rails app on Nitrous.IO

Login to Nitrious.IO and create or open up a Rails box. Within the console enter in the following commands:

    $ rails new blog
    $ cd blog

At this point you can test your Rails app with the following command:

    $ rails server

Once the app is running, you can view it by navigating to <strong>Preview > Port 3000</strong> in your Nitrous.IO IDE.

### Setting up the Database configurations

The next step is to configure the app to connect to Amazon RDS.

Within config/database.yml, configure your development environment to use the following variables:

    development:
     adapter: mysql2
     encoding: utf8
     database: <%= ENV['RDS_DB_NAME'] %>
     username: <%= ENV['RDS_USERNAME'] %>
     password: <%= ENV['RDS_PASSWORD'] %>
     host: <%= ENV['RDS_HOSTNAME'] %>
     port: <%= ENV['RDS_PORT'] %>

For our test and production databases, we'll be provisioning new databases on Amazon RDS. If you want to create a test database ("blog-app-test"), just repeat these instructions.

As you can see we have changed the adapter to use mysql2 which is the adapter Amazon RDS uses. You will also need to install the following gem in order to add support for this:

    $ gem install mysql2
    $ bundle install

Add the mysql2 gem to your Gemfile:

    gem 'mysql2'


### Creating the Database

The App should now have access to the Amazon RDS instance. Run the following commands to create a new database, create a new table, and migrate it to Amazon RDS:

    $ rake db:create
    $ rails generate controller home index
    $ rails generate scaffold Post name:string title:string content:text
    $ rake db:migrate

### Configuring your Routes and Adding a Link

You will first need to remove your static index file:

    $ rm public/index.html

Add the following route into config/routes.rb:

    Blog::Application.routes.draw do
      root :to => "home#index"
    end

Open app/views/home/index.html.erb and modify it to include the following code:

    <h1>Hello, Rails!</h1>
    <%= link_to "My Blog", posts_path %>

### Previewing the App

Once the database is successfully migrated, run the following command:

    $ rails server

You can now view the Rails App by navigating to <strong>Preview > Port 3000</strong> in your Nitrous.IO IDE.

For our regular users: How'd it go for you? If you're having trouble, you can always get in touch with us by visiting our [chatroom](https://action.io/chat) or by [emailing us](mailto:support@action.io).
