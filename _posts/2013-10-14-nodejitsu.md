---
title: Deploying to Nodejitsu
published: true
categories: [deployment]
layout: article
---

These instructions will help you deploy your [node.js](http://nodejs.org/) application to [Nodejistu](http://www.nodejitsu.com/?ref=nitrous.io).

### Things you should know

* Node.js basic concepts. Your Nitrous.IO box will come preinstalled with Node.js.

### Prerequisites

* An [Nitrous.IO Account](https://www.nitrous.io)
* A [Nodejitsu Account](https://www.nodejitsu.com/signup/?ref=nitrous.io) or sign up below.
* A [Node.js box](https://www.nitrous.io/app#/boxes) on Nitrous.IO
* Any Node.js project. [See an Example here](/azure-sites/) 


### Install jitsu Command Line Interface (CLI)

The [jitsu CLI](https://www.nodejitsu.com/documentation/jitsu/) allows you to connect to the nodejitsu platform right from Nitrous.io  
Install it by running the following command in the Nitrous.io console:
    
    npm -g install jitsu
    
### Sign up for nodejitsu (Optional) 
 
If you don't already have a nodejitsu account, run the following command to signup:
    
    jitsu signup

### Login to nodejistu

Login with following command and enter your nodejitsu username and password: 
    
    jitsu login
 
### Deploying rom Nitrous

To deploy simply issue the following command:   

    jitsu deploy

This will prompt you for your project name, the subdomain you wish use, and the project start script.  
Once your configuration is set and prjoect files are uploaded to nodejistu the command will return 'Nodejitsu ok'

At this point your can browse to **http://your-app-subdomain.nodejitsu.com** to see your app.

Happy coding.