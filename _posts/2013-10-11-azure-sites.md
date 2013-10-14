---
title: Deploying Node.js App to Azure Sites
published: true
categories: [deployment]
layout: article
---

These instructions will help you deploy your [node.js](http://nodejs.org/) application to [Azure](http://www.windowsazure.com/en-us/develop/nodejs/).

### Things you should know

* Node.js basic concepts. Your Nitrous.IO box will come preinstalled with Node.js.

### Prerequisites

* An [Nitrous.IO Account](https://www.nitrous.io)
* A [Windows Azure Subscription](http://www.windowsazure.com/en-us/pricing/free-trial/?ref=nitrous.io)
* A [Node.js box](https://www.nitrous.io/app#/boxes) on Nitrous.IO
* Any Node.js project with a git repo. We will use the snippet below for this excercise.

### Example Node.js App 

    //Example Node.js App
    //Save this to server.js in your project directory.
    var http = require('http')
    var port = process.env.PORT || 3000;
    var host = process.env.HOST || '0.0.0.0';
    http.createServer(function(req, res) {
      res.writeHead(200, { 'Content-Type': 'text/plain' });
      res.end('Hello World from Nitrous.IO\n');
    }).listen(port, host);
    console.log("Server running at "+host+":"+port);

If you don't have a project ready to go save the code above into your project directory into a file called *server.js* 

If you're not already using git, you need to configure git,  setup a new repo and make an initial commit by running the follwing commands in your project directory: 

    git config --global user.email “(your git email)”
    git config --global user.name “(your git username)”
    git init
    git add . 
    git commit -am "initial commit"

### Testing your Node.js App

You can test your app out locally by running the following command in the console, replacing 'your_app/server.js' with your app:

    node  your_app/server.js

The app is now running and you will be able to preview it by navigating in the toolbar to **Preview > Port 3000**.

### Install Azure Command Line Interface (CLI)

The [Azure CLI](http://www.windowsazure.com/en-us/manage/install-and-configure-cli/) allows you to  maniupulate your Azure Sites right from Nitrous.io  

Install it by running the following command in the Nitrous.io IDE console:
    
    npm -g install azure-cli 

### Connect to your Azure Subscription

Now let's connect this CLI to your Azure Subscription.

Run the following command in the console to download your credentials from Azure: 
    
    azure account download

 
Open a new browser window and go to the link that is returned by the previous command. 
After you login, a `.publishsettings` credentials file will be downloaded to your machine. 

Upload this file to you Nitrous IDE using the [Upload Files button](http://help.nitrous.io/ide-file-uploads/) and run the following command replacing **pathto/mysubscription.pubishsettings** with the appropriate path to the credentials file:

    azure account import pathto/mysubscription.pubishsettings

    
### Create a New Azure Site

To create a new Azure Site change to your **project directory** and run the following command: 
    
    azure site create my_project_name --git

This will create a basic site with a git repository on the host and add the Azure Site repo as a remote to your local **project directory** repo. 

You can confirm that this worked by going to the hostname returned by the command.

![New Azure App](/images/articles/azure-new-app.png)

### Deploying From Nitrous

To deploy simply push your commited code to Azure Sites with the following command:   

    git push azure master

You will now be prompted to enter in your Azure Account password.

Once the upload has finished you should see the message "Deployment Successful". 
Then browse directly to your live application at http://appname.azurewebsites.net.
