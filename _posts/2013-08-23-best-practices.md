---
layout: article
title: "Best Practices"
published: true
categories: [getting started, web ide]
---

You have gone through our [Getting Started Guide](/getting-started/), and can now [SSH](/ssh-add/) from your computer as well as connect to Github. Now the question is, what's the best way to use Nitrous.IO?

### Building Projects

You can create as many projects as you would like within a single Nitrous box. The only limitations to this is the amount of storage space you use, which not only counts the project files but also modules, different versions of Ruby installed, etc.

Below you will see a screenshot of how you could setup your directories within Nitrous. All projects should be places within the `~/workspace` folder, and configuration files can be placed in your home directory `~/`.

![Nitrous Box Directory](/images/articles/directory-tree.png)

### Previewing an App

Once you have built an app (ex. a [Meteor app](http://blog.nitrous.io/2013/02/21/build-meteor-apps-in-the-browser-with-actionio-and-mongolab.html) or a [Rails app](http://blog.nitrous.io/2013/07/02/building-a-rails-4.0-app-on-nitrous-io.html)), you will want to run the app with the appropriate command within the console. Here is an example of running a Rails app with the command `rails server`:

		action@ruby-rails-10201:~/workspace/projects/rails-app$ rails server
		=> Booting WEBrick
		=> Rails 4.0.0 application starting in development on http://0.0.0.0:3000
		=> Run `rails server -h` for more startup options
		=> Ctrl-C to shutdown server
		[2013-08-23 18:12:48] INFO  WEBrick 1.3.1
		[2013-08-23 18:12:48] INFO  ruby 2.0.0 (2013-05-14) [x86_64-linux]
		[2013-08-23 18:12:48] INFO  WEBrick::HTTPServer#start: pid=8021 port=3000

Nitrous has HTTP ports 3000 - 9000 open, so you can use any of these ports when previewing your app.

Since this app is running on Port 3000 we will navigate in the web IDE to `Preview > Port 3000` to view the app running in the browser.

![Preview App](/images/articles/preview-port-3000.png)

If you need to switch to a different port, you can do this by editing the URL in the address bar.

![Changing the Port](/images/articles/address-bar-port.png)

### Using the IDE Console

If you prefer to work within the console, you can make it fullscreen within the web IDE by pressing `Shift + Ctrl + F`.

![Fullscreen Console](/images/articles/web-ide-fullscreen.png)

### Connecting via SSH

If you want to work from your local console you can use [SSH](/ssh-add/). One easy strategy for Mac users would be to use [iTerm 2](http://www.iterm2.com/) and setup a `Profile` with your SSH credentials. To setup a profile, navigate to your [boxes](https://www.nitrous.io/app#/boxes) page and copy your SSH URI:

![SSH URI](/images/articles/ssh-uri.png)

Next, open up Iterm2 and navigate to **Preferences > Profiles**. Create a new profile and fill in your SSH URI into the **Command** field. The format should be `ssh action@YOUR_REGION.actionbox.io -p YOUR_PORT`

![Iterm 2 Profile](/images/articles/iterm2-profile.png)

>Tip: In the iTerm2 Profile settings you can also assign a Shortcut key to launch your Nitrous SSH session.

### Working locally

If you want ability to use [Sublime Text](http://www.sublimetext.com/) or any other editor, you will want to work locally and sync with your Nitrous box.

Nitrous offers a [Mac app](http://www.nitrous.io/mac) to do this, with Windows and Linux support coming soon.

For help using the Mac App please view the [Mac preferences guide](/mac-preferences/).
