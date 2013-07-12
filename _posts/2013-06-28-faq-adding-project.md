---
layout: article
title: Upload an existing application
published: true
categories: [faq, getting-started]
---

We get a lot of emails asking how to upload applications to an Nitrous.IO box. There are many ways to do this; using SCP, installing the [Mac App](https://www.nitrous.io/mac), and in this guide SFTP and Git.

### Uploading your project via SFTP

Uploading via SFTP requires that you have set up your public / private keypair on your machine and added your public key to Nitrous.IO. To do this, we recommend that you use PuttyGen. Visit this link and look for the PuttyGen download:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

![PuTTYgen](https://raw.github.com/action-io/action-assets/master/support/screenshots/puttygen.png)

Click the **PuTTYgen.exe** link to download the application.

Open PuTTYgen and click the **Generate** button next to "Generate a public/private keypair".

![keygen button](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-keygen.png)

You'll be asked to move your mouse around to help PuTTY generate a random keypair for you.

![keygen random](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-random.png)

Once your keys are generated, you'll want to save them someplace private. Click the "Save Public Key" and "Save Private Key" buttons to save the files.

![putty save keys](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-key.png)

PuTTY will automatically save the private key as a .ppk file, which is a putty private key file that contains some additional encoded information about your key. Keep the .ppk extension for this file.

Name the public key something like **public_key.pub** and the private key **private_key.ppk** and save them someplace safe.

>You want to save these keys someplace safe because if someone were to find your private key, they could authenticate with any services where you utilize public key authentication.

Okay, so now we have our keypairs set up, let's go ahead and add our public keys to Nitrous.IO.

1. Signin to your [Nitrous.IO](https://nitrous.io) account
2. Click the "Public Keys" link in the top navigation
3. Create a name for your public key -- something that identifies the machine. I'll use "AJ's Windows XP".
4. Paste your public key in the text area.

![action key](https://raw.github.com/action-io/action-assets/master/support/screenshots/win-key.png)

### Download SFTP Client

Next, you'll need to download an SFTP client. For this article we'll use [Filezilla](http://filezilla-project.org/), but if you're on a Mac you can also check out [Transmit](http://panic.com/transmit/). Filezilla is free, so go ahead and download it now.

![filezilla download](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-win-download.png)

Now we need to tell Filezilla to connect via SSH using our SSH keypair that we just generated. First, click **Edit > Settings** in the top menu.

![filezilla settings](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-settings.png)

Once in the settings pane, click **Connection > FTP > SFTP** and click the **Add keyfile...** button.

![filezilla settings sftp](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-sftp.png)

Then we'll want to add the private key that we just created and put in our safe folder.

![filezilla settings sftp privatekey](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-privatekey.png)

Then click the **OK** button.

### Setup site profile to connect to Nitrous.IO

Ok, now that we've added the key to Filezilla, lets go ahead and add the connection details.

#### 1. Click File > Site Manager in the application menu

![filezilla site manager](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-sitemanager.png)

#### 2. Click the **New Site** button and name the connection profile. I'm going to name it the same as my box on Nitrous.IO

![filezilla new site](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-newsite.png)

#### 3. Type in **action** as the username and the relevant **host** and **port** information from your box details page on Nitrous.IO:

![filezilla box details](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/box-details.png)

* Protocol: SFTP - SSH File Transfer Protocol
* Logon Type:  Normal
* User: action
* Password: \[leave blank\]
* Account: \[leave blank\]

Then click the **Connect** button. You might see an alert box telling you the host is unknown. Click the checkbox to let filezilla know this is a trusted host, and click OK.

![filezilla unknown host](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/host-unknown.png)

You'll see the connection details streaming in the filezilla status menu and then you should see that you're all connected! Congratulations!

![filezilla connected](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/filezilla-connected.png)

### Uploading your project via Git

If you have git installed on your machine, you can easily push a code repository to github (or another repository hosting service), then clone the repository on your Nitrous.IO box.

Prerequisites:

* Installed [Git](http://git-scm.com/)
* Working knowledge of [Git commands](http://try.github.com/levels/1/challenges/1)

Read this article about how to connect your github account to Nitrous.IO:

**Mac:**
[Adding your keys to Github](/github-add-key)

**Windows:**
[Adding SSH Keys on Windows](/ssh-windows)

Once you've successfully setup your SSH keys, you can easily clone repositories from Github to your Nitrous.IO boxes.

