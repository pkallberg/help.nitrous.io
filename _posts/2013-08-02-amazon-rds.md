---
layout: article
title: Amazon RDS
published: true
categories: [databases]
---

With [Amazon RDS](http://aws.amazon.com/rds/) you can quickly and easily provision and maintain a MySQL, Oracle, or Microsoft SQL Server instance in the cloud.

### Prerequisites

* A Nitrous Box within the same region as the database you will create. View the [Regions Settings](/faq-aws-region-settings/) guide for more information on this.
* You will need to first sign up with [Amazon Web Services](http://aws.amazon.com/).


### Adding a Security Group with Amazon RDS

Login to your [Amazon RDS Console](https://console.aws.amazon.com/rds/home), navigate to Security Groups and create a new Connection Type with the following EC2 Security Group Details:

    AWS Account ID: 643018315983
    EC2 Security Group (name): box_host

![Security Group Details](/images/articles/amazon_rds_security_group.png)

###  Setting Up a New Instance with Amazon RDS

Within your [Amazon RDS Console](https://console.aws.amazon.com/rds/home) you will want to navigate to Instances and Launch a new DB Instance. When prompted, select the MySQL Database Engine. 

On the Additinal Configuration page, ensure the **Availability Zone** matches the region of your Nitrous box. In this example, the Nitrous box is in the US West region and we have selected **us-west-1a** for the Availability Zone.

Select the DB Security Group you have just created, and also remember your password for connecting later.

![Amazon RDS Settings](/images/articles/amazon_instance_setting.png)

### Setting up the Database configuration (Ruby/Rails)

If you are building a Rails app, follow this step to connect your app to Amazon RDS. 

In the Instances tab of your [Amazon RDS Console](https://console.aws.amazon.com/rds/home), you will see all of the database credentials needed to login (except for your password which you created):

![Amazon RDS Instance Settings](/images/articles/amazon-rds-instance-details.png)

Grab each of the values and assign them to environment variables in your
"~/.bashrc" file on your Nitrous.IO box. This will ensure that every time you log into your Nitrous.IO box, your
database credentials will be available as environment variables to use
in any of your apps. It is good practice to namespace your environment
variables with the environment that you want to use your database in
(development or test), like so:

![Env Variables](/images/articles/rds-bashrc.png)

If you want the environment variables to be loaded immediately, run:
    source ~/.bashrc

Within config/database.yml, configure your development environment to use your database instance's configuration details:

    development:
     adapter: mysql2
     encoding: utf8
     database: <%= ENV['RDS_DB_NAME'] %>
     username: <%= ENV['RDS_USERNAME'] %>
     password: <%= ENV['RDS_PASSWORD'] %>
     host: <%= ENV['RDS_HOSTNAME'] %>
     port: <%= ENV['RDS_PORT'] %>

>Note: If you wish to configure test and production databases, you will want to provision new databases on Amazon RDS.

As you can see we have changed the adapter to use mysql2 which is the adapter Amazon RDS uses. You will also need to install the following gem in order to add support for this:

    $ gem install mysql2

Also, you will want to add the mysql2 gem to your Gemfile:

    gem 'mysql2'
