---
layout: article
title: Installing Databases and Tools with Autoparts
published: true
categories: [databases, usage]
---

Autoparts is a package manager for Nitrous.IO which allows you to install databases and other tools on your box within your home folder.

### Installing Autoparts

Autoparts is available on all boxes with version `bran` which were created after 9-17-2013.

Run the following command in your terminal to see if Autoparts is installed:

    parts

If you do not see information for the Autoparts package manager you can install it with the following two commands:

    ruby -e "$(curl -fsSL https://raw.github.com/action-io/autoparts/master/setup.rb)"
    exec $SHELL -l

You can also check the [boxes page](https://www.nitrous.io/app#/boxes) to see which version you are running on. The screenshot below shows version `bran` under the stack information:

![Bran version Nitrous Box](/images/articles/bran-box.png)

### Updating Autoparts

New tools, interpreters, and databases are always being added to Autoparts. To update Autoparts with the latest changes, run the following command:

    parts update

### Installing a Package

To view all of the packages available to install, run the following command:

    parts search

This will bring up a list including the following tools:

    memcached (1.4.15)         Memcached: An open-source, high-performance...
    meteor (0.6.5.1)           Meteor: A real-time web development platform
    mongodb (2.4.6)            MongoDB: A cross-platform document-oriented...
    mysql (5.6.13)             MySQL: The world's most popular open-source...
    phantomjs (1.9.1)          PhantomJS: A headless WebKit scriptable wit...

Ex: To install MySQL, run the following command:

    parts install mysql