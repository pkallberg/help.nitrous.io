---
layout: article
title: Add SSH keys (windows)
published: true
categories: [ssh, public keys, windows]
---

SSH Keys enable you to manage your Nitrous boxes directly from your computer via your favorite SSH client.  The keypair is used to identify you when interacting with your box from outside of [our website](https://www.nitrous.io).

<ul class="inline choices">
  <li><a href="/ssh-add/">Mac</a></li>
  <li class="selected">Windows</li>
</ul>

On Windows, we recommend that you use [PuttyGen](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html). Visit this link and look for the PuttyGen download:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

![PuTTYgen](https://raw.github.com/action-io/action-assets/master/support/screenshots/puttygen.png)

Click the **PuTTYgen.exe** link to download the application.

Open PuTTYgen and select the **SSH-2** RSA within the parameter settings. The "Number of bits in a generated key" field should be **2048**. Once these settings are selected, click the **Generate** button next to "Generate a public/private keypair".

![keygen button](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-keygen.png)

You'll be asked to move your mouse around to help PuTTY generate a random keypair for you.

![keygen random](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-random.png)

Once your keys are generated, you'll want to save them someplace private. Click the "Save Public Key" and "Save Private Key" buttons to save the files.

![putty save keys](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty-key.png)

PuTTY will automatically save the private key as a .ppk file, which is a putty private key file that contains some additional encoded information about your key. Keep the .ppk extension for this file.

Name the public key something like **public_key.pub** and the private key **private_key.ppk** and save them someplace safe.

<p class="note">You want to save these keys someplace safe because if someone were to find your private key, they could authenticate with any services where you utilize public key authentication.</p>

Okay, so now we have our keypairs set up, let's go ahead and add our public keys to Nitrous.IO.

1. Signin to your [Nitrous.IO](https://www.nitrous.io) account
2. Click the "Public Keys" link in the top navigation
3. Create a name for your public key -- something that identifies the machine. I'll use "AJ's Windows XP".
4. Paste your public key in the text area and click **Add Key**.

>Note: The Putty Key Generator may add a line similar to 'the comment: "rsa-key-20130101"' to your public RSA key. You will need to remove this line before pasting it into the text area within your Nitrous.IO account.

![action key](https://raw.github.com/action-io/action-assets/master/support/screenshots/win-key.png)

Now let's connect to one of our development boxes. For this, we're going to use the [PuTTY SSH client](http://www.chiark.greenend.org.uk/~sgtatham/putty/).

![putty download](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty/putty-dl.png)

Once you've downloaded, open up the application. On the left pane, you'll need to navigate down to **Connection > SSH > Auth**

![putty auth](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty/putty-auth.png)

Now we're going to tell PuTTY where to find our private key. Click on the **Browse** button, and navigate to the safe folder where you saved your public key above.

![putty key](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty/putty-privatekey.png)

Select your private key, and click **Open**

Back on the PuTTY pane, click **Session** at the top. You'll see all of the required connection information. You'll need to type in your hostname, port, and make sure the connection type is set to SSH. You can find the hostname and port information on the [Nitrous.IO](https://www.nitrous.io/boxes) website in the box details pane.

Your hostname will be something like:  **apse1.actionbox.io** and your port will be at the end of the string after the colon:

![box details](https://raw.github.com/action-io/action-assets/master/support/screenshots/sftp/box-details.png)

You'll probably want to enter a name into the input under the **Saved Sessions** label. Since the box I'm connecting to is called Bonzai on Nitrous.IO, I'm going to call this session "Bonzai" and click Save to save the session to my list of saved profiles.

Now, let's try out the connection. With our Bonzai profile loaded, click the **Open** link at the bottom of the window. An SSH terminal should appear. When it asks you who to login as, just type "action". This is the common user for free boxes.

    login as: action

Then hit enter, and you should see the message:

    Authenticating with public key "rsa-key-[date]"

And we'll see that we're successfully connected to our box!

![connected](https://raw.github.com/action-io/action-assets/master/support/screenshots/putty/putty-term.png)

Of course, if you're having trouble, you can always [talk to a real human](mailto:support@nitrous.io?subject=SSH%20Key%20Issues%20Windows).
