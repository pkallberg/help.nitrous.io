---
layout: article
title: Add SSH key to github
published: true
categories: [ssh, public keys]
---

For those developers using [Github](http://github.com), Action lets you easily add your box's ssh keys so managing your repositories is a breeze.

### 1. Connect your Github Account

First, you'll need to authenticate your Github account so we're allowed to add ssh keys to your profile on Github.

In the top navigation, click your N2O meter bar which will take you to the [bonus page](https://www.nitrous.io/app#/n2o/bonus).

![N2O Bonus Page](/images/articles/n2o-bonus-page-github.png)

On the Bonus page, click the "Connect to Github" button.

You'll be redirected to the Github authentication page, where you can review the policies and select "Allow".

You will then be redirected back to Nitrous.IO and you should see a message that you've authenticated successfully. If you're having trouble, send us an email.

### 2. Add Box SSH Key to Github

Now that you've successfully authenticated your Github account, you'll be able to add your SSH keys from your Nitrous.IO to your Github account.  This will allow you to easily work with your repositories on Github.

Navigate back to the Boxes page, by clicking the "Boxes" link in the top navigation.

Click any of your boxes to toggle it's details and click the "Reveal Public Key" link.

![Reveal Public Key](https://raw.github.com/action-io/action-assets/master/support/screenshots/reveal-public-key.png)

Once your public key is revealed, you simply need to click the "Add to Github" link to the right of the key.  After a few seconds, you should see the link be replaced with a status message that reads "Added to Github!"

And that's it! Keys on Github will be named "actionio-\[boxname\]".

### 3. Confirming Key is Added (Optional)

If you want to confirm that your SSH key from your action box has been added to Github or want to remove the key, sign in to your Github account and click the "Account Settings" link in the top right navigation and then "SSH Keys" on the left nav.

_Account Settings >> SSH Keys_

You should see the key you added via Nitrous.IO.

![Action Box Key](https://raw.github.com/action-io/action-assets/master/support/screenshots/github-action-key.png)
