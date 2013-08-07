---
title: Deploying to App Engine
published: true
categories: [deployment]
layout: article
---

These instructions will help you deploy your [Python](https://www.djangoproject.com/) application to [App Engine](https://cloud.google.com/console?getstarted=https://appengine.google.com).

### Things you should know

* Python basic concepts. Your Nitrous.IO box will come preinstalled with Python and App Engine.

### Prerequisites

* An [Nitrous.IO Account](https://www.nitrous.io)
* A [Google Cloud Account](https://developers.google.com/appengine/)
* A [Python box](https://www.nitrous.io/app#/boxes) on Nitrous.IO
* A project built for App Engine. View the [Google Cloud Github Repo](https://github.com/GoogleCloudPlatform/appengine-guestbook-python) for an example.

### Testing your Python app

You can test your app out by running the following command in the console, replacing **your_app/** with the directory which your app resides in:

    dev_appserver.py --host=0.0.0.0 --port=3000 your_app/

The app is now running and you will be able to preview it by navigating in the toolbar to **Preview > Port 3000**.

### Registering your app

In the [Cloud Console](https://cloud.google.com/console?getstarted=https://appengine.google.com), create a new app. You should be prompted to enter in your Project Name and **Project ID**. Copy down the **Project ID** for the next step.

![New App Engine App](/images/articles/appengine-new-app.png)

### Deploying From Nitrous

Within your project, open `app.yaml` in an editor. change the value of the `application:` setting from `your-app-id` to your **Project ID**.

![app.yml settings](/images/articles/app-engine-appyml.png)

Now you are ready to deploy to App Engine. Run the following command in
your console, replacing the directory with your actual project
directory:

    appcfg.py update ~/workspace/directory_of_your_project

You will now be prompted to enter in your Google Accounts's email and
password.

Once the upload has finished you should see the message "Deployment
Successful". Then browse directly to your live
application at http://application-id.appspot.com.

> You can also use [Git to push and deploy](https://developers.google.com/appengine/docs/push-to-deploy)
