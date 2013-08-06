---
layout: article
title: Regions within AWS
published: true
categories: [faq]
---

### Setting Up Regions Within Amazon Web Services

When connecting to Amazon Web Services within your Nitrous box, both your Nitrous box and the AWS region will need to be the same. When provisioning a new Nitrous box you will be prompted to connect to a specific region:

![Nitrous Box Region](/images/articles/nitrous-regions.png)

You can change regions within (Amazon Web Console)[] by logging in and clicking on your current region in the top right hand side of the toolbar:

![AWS Region Settings Toolbar](/images/articles/amazon-regions.png)

Once this has been setup to match the same region as your Nitrous box, future databases you create within AWS will provide you with the option to select an Availability Zone within that region.

### Creating a Security Zone

Along with creating a database within the same region as your Nitrous box, you will also need to add a **Security Zone**.

To Utilize a database within AWS, you will need to setup the following Security Group Details. For example, to setup an RDS database, login to your [Amazon RDS Console](https://console.aws.amazon.com/rds/home), navigate to Security Groups, and create a new Connection Type with the following EC2 Security Group Details:

    AWS Account ID: 643018315983
    EC2 Security Group (name): box_host

>Note: These settings are the same for all regions.

### Connecting to a Database

You will need to ensure the following steps are completed before creating a database:

*Your Nitrous box and AWS account are set for the same region
*You have created a **Security Group**

In the [Amazon RDS Console](https://console.aws.amazon.com/rds/home), click **Launch DB Instance**. From here you will be prompted to configure your new database.

On the **Additinal Configuration** page, ensure the **Availability Zone** belongs to the region of your Nitrous box. In this example, the Nitrous box is in the US West region and we have selected **us-west-1a** for the Availability Zone. Notice that the DB Security Group has been selected as well.

![Amazon RDS Settings](/images/articles/amazon_instance_setting.png)

For a full guide on connecting to Amazon RDS, please view the [Amazon RDS guide](/amazon-rds).