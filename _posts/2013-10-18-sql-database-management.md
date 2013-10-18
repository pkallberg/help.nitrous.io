---
layout: article
title: Connecting to MySQL with a SQL Database Management App
published: true
categories: [databases]
---

This guide will walk you through the steps to connect [Sequel Pro](http://www.sequelpro.com/) to your MySQL database created via [Autoparts](/autoparts/).

### Prerequisites

* A Nitrous.IO box with a MySQL database created. View the [MySQL Guide](/mysql/) if you have not done this already.
* A Database Management App. [Sequel Pro](http://www.sequelpro.com/) is a great tool for Mac users.

### Setting up Port Forwarding

#### If you are using the Nitrous [Mac App](http://www.nitrous.io/mac): 

Within the Menu Bar, open up the App Preferences, navigate to `Port Forwarding`, and check the box `Enable Port Forwarding`. 

From here, add port 3306 to the list of forwarded ports as this is the default port for MySQL.

![Enable Port Forwarding](/images/articles/port-forwarding-port-3306.png)

#### If you are not using the Nitrous App:

Within your local console, run the following command to establish SSH tunneling between your local port and the remote port:

    ssh -N -p <box_port> action@<box_host> -L <local_port>/localhost/<remote_port>

When running this command, replace the variables with the actual values found on your boxes page. This is an example command which would be used for the box information seen in the image below:

    ssh -N -p 71717 action@usw1.actionbox.io -L 3306/localhost/3306

![Nitrous Box Connection Info](/images/articles/nitrous-box-connection-info.png)

> Tip: You can check which port your database is running on by running `netstat -anp | grep -i mysql` within your Nitrous console.

### Connecting with Sequel Pro

Once you have installed [Sequel Pro](http://www.sequelpro.com/), open up the app and connect to host `127.0.0.1` on port `3306`.

![Sequel Pro Connection Details](/images/articles/sequel-pro.png)

You should now be connected to the database hosted on Nitrous.IO.
