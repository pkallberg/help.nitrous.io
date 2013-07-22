---
layout: article
title: Getting Started with Nitrous.IO
published: true
categories: [getting started]
---

Our goal is to provide you with a streamlined, beautiful and, enjoyable programming experience.

If you have any problems setting things up, check out [help.nitrous.io](http://help.nitrous.io) or send us an email at support at action dot io.

### 1. Sign Up for an Account

Our beta period is invite-only, so if you haven't received an invite, you can signup for our beta list on our [homepage](https://nitrous.io).

If you've received the beta invite email, just click the link in the email and fill out a username and password.  We'll use the username around the site and to identify your boxes so pick something you like.

### 2. Create a box

Once you've signed in to the site, you'll see your dashboard. You won't have any boxes created yet, so go ahead and click "New Box". If you need help creating a box, you can follow [these instructions](/box-new).

### 3. Adding SSH Keys to your Action Box

Adding your local SSH keys to your remote Action box will allow you to SSH into your box from Terminal / PuTTY etc…. This is great for developers who use Vim or Emacs.

If you're not already using SSH, this article can walk you through the steps required:

[Adding SSH Keys to your Nitrous.IO Account](/ssh-add)

To test out whether you've added your keys directly, click your box in the dashboard to toggle its details and click the SSH URI link:

![Box Details](https://raw.github.com/action-io/action-assets/master/support/screenshots/box-details.png)

Your browser will attempt to open a local terminal session. If there's a prompt like this, just click "Allow":

![SSH Prompt](https://raw.github.com/action-io/action-assets/master/support/screenshots/ssh-confirm-prompt.png)

In your terminal, you should see something like this:

<pre class="">
  The authenticity of host '[apse1.actionbox.io]:10253 ([54.251.42.128]:10253)' cant be established.
  RSA key fingerprint is 57:b7:dd:50:04:09:e8:f8:e5:93:e1:2d:2f:46:a5:f5.
  Are you sure you want to continue connecting (yes/no)? yes
</pre>

Type "yes", which will add your Action box to your known_hosts ssh file.

<pre class="">
Warning: Permanently added '[apse1.actionbox.io]:10253, [54.251.42.128]:10253' (RSA) to the list of known hosts. Welcome to Nitrous.IO (GNU/Linux 3.2.0-31-virtual x86_64)
</pre>

Now go ahead and poke around-- you should be in your remote box on Nitrous.IO!

### 4. Add Action Box SSH Keys to Github

So we've got our development box built, but what if we want to get a project we've been working on into our box on Action?

Adding SSH Keys to Github is super easy, just check out the steps in the following article:

[Adding SSH Keys to Github](/github-add-key)

Now, you can go back to your Nitrous.IO box in your local terminal or in the Nitrous.IO Web IDE and can clone any of your Github repos.

[Now you rollin'](http://www.youtube.com/watch?v=CtwJvgPJ9xw&t=0m14s).
