---
layout: article
title: Building a Meteor App
published: true
categories: [tutorials, node]
---

### Prerequisites

* A Node.JS box on [Nitrous.IO](http://www.nitrous.io)

### Installation

Meteor can be installed on the Nitrous box via [Autoparts](http://help.nitrous.io/autoparts/). Within the console, run the following command:

    parts install meteor

This will setup a Meteor installation along with MongoDB.

### Creating a New Meteor App

To start a new project, run the following command:

    meteor create meteorapp

Navigate into the project folder and run the app with these two commands:

    cd meteorapp
    meteor

After a moment you should see that the app is running on port 3000. Navigate in the menu bar to **Preview > Port 3000**.

![Preview Port 3000](/images/articles/preview-port-3000.png)

This will bring up a new tab with the running app. It should resemble the screenshot below:

![Preview Meteor App](/images/articles/meteor-preview-app.png)

You can keep this browser tab open as Meteor will watch for file changes, and will automatically refresh the page after changes are made.

Within your project folder you will see a CSS, HTML, and JS file. Let's delete these as we will create our own in a moment.

    rm *.html *.css *.js

### Client and Server Code

In order for Meteor to keep track of which JavaScript is meant only for the client or server, we will create two separate directories; the /client and /server:

    mkdir client
    mkdir server

Within the `/client` folder, create a `index.html` and `style.css` file.

    cd client
    touch index.html style.css

### Add Twitter Bootstrap to Your Project

You can stylize your app with Bootstrap by running the following command

    meteor add bootstrap

From here, edit your `style.css` file to include the following CSS:

    body {
      padding-top: 60px;
    }

Notice how there is no CSS from bootstrap in the main project directory. Meteor handles this automatically, and if you need to make any CSS changes then you can override it within the `style.css` file.

Next, edit `client/index.html` to include only the following code:

     <head>
       <title>Meteor on Nitrous.IO</title>
     </head>
     <body>
     <div class="navbar navbar-inverse navbar-fixed-top">
           <div class="navbar-inner">
             <div class="container">
               <button type="button" class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse">
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
               </button>
               <a class="brand" href="#">Project name</a>
               <div class="nav-collapse collapse">
                 <ul class="nav">
                   <li class="active"><a href="#">Home</a></li>
                   <li><a href="#about">About</a></li>
                   <li><a href="#contact">Contact</a></li>
                 </ul>
               </div><!--/.nav-collapse -->
             </div>
           </div>
         </div>
         <div class="container">
           <h1>Login to continue</h1>
           <p>{% assign loginButtons = '{{loginButtons}}' %}
             {{ loginButtons }}
           </p>
        </div>
    </body>

Notice the block `{{ loginButtons }}` within the code. Meteor supports Handlebars templating, which allows us to many things. In this case we are going to utilize this block to call the Meteor Accounts system. Run the following commands to install the login service:

    meteor add accounts-password
    meteor add accounts-ui

If you still have the browser open then you should see the page refresh to look like the screenshot below:

![Meteor Login Page](/images/articles/meteor-login-page.png)

At this point you should be able to test out the login form by clicking sign in, followed by create account. Sign up with a email and password so successfully sign in.

![Create User with Meteor](/images/articles/meteor-app-create-user.png)

To test this further, let's add the following code to display only if a user is logged in. Update `client/index.html` to include the following code:

    <head>
       <title>Meteor on Nitrous.IO</title>
     </head>
     <body>
     <div class="navbar navbar-inverse navbar-fixed-top">
           <div class="navbar-inner">
             <div class="container">
               <button type="button" class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse">
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
               </button>
               <a class="brand" href="#">Project name</a>
               <div class="nav-collapse collapse">
                 <ul class="nav">
                   <li class="active"><a href="#">Home</a></li>
                   <li><a href="#about">About</a></li>
                   <li><a href="#contact">Contact</a></li>
                 </ul>
               </div><!--/.nav-collapse -->
             </div>
           </div>
         </div>
         <div class="container">
           <h1>Login to continue</h1>
           <p>{{ loginButtons }}</p>
           <p>{% assign ifcurrentuser = '{{#if currentUser}}' %}{% assign if = '{{/if}}' %}
             {{ ifcurrentuser }}
               You are now logged in.
             {{ if }}
           </p>
        </div>
    </body>

In the `index.html` file, we just added the `{{ ifcurrentuser }}` logic to state that "you are now logged in" only when you are signed in. Once you save the file, the page will refresh with the changes.

![Meteor App Logged In](/images/articles/meteor-logged-in.png)

Test this out by signing in and out of the login form. The text will only display when logged in.

### Deployment

Deployment with Meteor is simple! You can use Meteor's free service to do this with the following command:

    meteor deploy meteorapp.meteor.com

Once this is ran, you should see the following if your subdomain is available, and everything was deployed successfully:

    /meteorapp $ meteor deploy meteorapp.meteor.com
    Deploying to meteorapp.meteor.com.  Bundling...
    Uploading...
    Now serving at meteorapp.meteor.com

Open the web browser to `http://YOUR_APP_NAME.meteor.com` to view your site.