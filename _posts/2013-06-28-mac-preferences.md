---
layout: article
title: Mac preferences
published: false
categories: [faq, mac]
---

Your Nitrous.IO for Mac preferences allow you to configure the connection between your computer and your boxes running on Nitrous.IO. For example, you can add/remove SSH keys, setup tunneling to preview applications you are developing, and manage shared folders for local editing.

### Accessing Nitrous.IO for Mac preferences on Mac OS X

1. Click on the Nitrous.IO icon in your menu bar

![Mac Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/mac/mac-menu.png)

2. Select *Preferences…* from the menu

### General

This displays the current version of your Nitrous.IO for Mac installation. Reference this number in [support requests](mailto:support@nitrous.io?subject=Mac%20Application) or to see if you have the latest version of Nitrous.IO for Mac. This tab will also contain basic notification and startup settings in future releases.

### Account

The username and full name (if applicable) associated with your Nitrous.IO account are displayed here. Your username, full name and other account settings can be viewed and edited on the [Nitrous.IO website](https://www.nitrous.io).

You can also sign out of the currently associated account. Note that this will force you to sign in again.

### SSH Keys

The application will automatically detect your SSH keys on your local computer. You will see the path to your private and public keys.

![Mac SSH Keys](https://raw.github.com/action-io/action-assets/master/support/screenshots/mac/mac-sshkeys.png)

*Generating a new Key*

If you do not have a public and private key, you can click the **Generate** button to create one. The application will create a key on your behalf and will save it by default to

    ~/.ssh/id_rsa (private key)
    ~/.ssh/id_rsa.pub (public key)

*Scanning for an existing key*

You can also tell the application to look for your key or get a new key if you've regenerated one manually by clicking the **Rescan** button.

### Tunneling

Tunneling allows you to forward ports to your

![Mac Tunneling](https://raw.github.com/action-io/action-assets/master/support/screenshots/mac/mac-tunneling.png)

To be able to tunnel to your Nitrous.IO box, you must first select the box from the list on the left of the preference pane, and check the **Enable Tunneling** checkbox.

Next, click the **+** icon at the bottom of the pane and enter the local port, destination host, and destination port where you would like to forward.

Repeat these steps for each of the boxes where you'd like to setup tunneling.

### File Sync

File sync is the magic that allows you to edit code locally using Sublime Text, Textmate, Eclipse, etc…

On your Nitrous.IO boxes, we automatically create a folder in your home directory called *workspace*. Anything in this folder will be earmarked to sync with your *Nitrous.IO* folder on your local machine.

![Mac Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/mac/mac-actionfolder.png)

Within your Nitrous.IO folder, you'll see folders that sync the contents in *workspace* for any boxes that have File Synchronization enabled.

*Enabling File Synchronization*

In the File Sync preference pane, click the box name that you'd like to start syncing. Then click the **Enable File Synchronization* checkbox.

Repeat this for each of your Nitrous.IO boxes that you'd like to sync.

![Mac Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/mac/mac-file-sync.png)
