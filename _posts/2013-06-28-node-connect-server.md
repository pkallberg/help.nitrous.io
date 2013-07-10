---
layout: article
title: Run a static site with NodeJS
published: true
categories: [node, faq]
---

Using the "connect" npm package, you can serve static files easily with node. Make sure the "connect" npm package is installed first by running:

    npm install connect

and then use the following code:

    var connect = require('connect');
    connect.createServer(connect.static(__dirname)).listen(3000);

You can then run it by doing `node server.js` and your static files should be available at port 3000.

You can find shortcuts to your preview urls in the "Preview" menu at the top of the web IDE:

![Preview Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/preview-menu.png)

Or if you're not using the Web IDE, you can find it in your Box details:

![Preview URL](https://raw.github.com/action-io/action-assets/master/support/screenshots/box-preview-url.png)

Of course, if you're having trouble, you can always [talk to a real human](mailto:support@nitrous.io?subject=Node%20Server%20Issues).
