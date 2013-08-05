---
layout: article
title: Problems previewing my application
published: true
categories: [faq, previewing]
---

Due to the way we handle network configuration on boxes, you will not be able to bind http servers to localhost (127.0.0.1).

Your application will need to run on 0.0.0.0 or a specific IP address. Listening on port 3000 will allow you to use our preview menu for a shortcut.

### Node.js example

Setting up a hello world web server on port 3000 using node.js.

<pre class="prettyprint lang-javascript">
  var http = require('http');
  http.createServer(function (req, res) {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello World\n');
  }).listen(3000, '0.0.0.0');
  console.log('Server running at http://0.0.0.0:3000/');
</pre>

Then make sure to run your node server in the console (substitute your file name):

    node helloworld.js

### Python example

When running a simple development server with [Django](https://docs.djangoproject.com/en/dev/intro/), we recommend:

    python manage.py runserver 0.0.0.0:3000


### Python on Google App Engine

When running the development app server on [Google App Engine](https://developers.google.com/appengine/docs/python/gettingstarted/), we recommend:

    dev_appserver.py --host=0.0.0.0 --port=3000


### Previewing the application

We supply some sensible default ports to enable you to preview your work in the browser. You can get your preview link in 1 of 2 ways:

Launch the Web IDE for your box, click the "Preview" menu and select the port where your web server is running.

![Preview Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/preview-menu.png)

In your list of boxes, click the box name to toggle it's details, copy the Preview URL and paste it in your browser. Change the port to 3000 or the applicable port where your server is running.

![Box Preview URL](https://raw.github.com/action-io/action-assets/master/support/screenshots/box-preview-url.png)
