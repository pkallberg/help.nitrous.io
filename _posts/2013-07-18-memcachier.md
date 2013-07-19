---
layout: article
title: MemCachier
published: false
categories: [databases]
---

MemCachier manages and scales clusters of memcache servers so you can focus on your app.

To get started, sign up with [MemCachier](http://memcachier.com/). You will need to select EC2 instance as well as a plan.

### Configuring Your App

Create a new app and use the following settings for AWS:

    security group id: box_host
    owner_id: 643018315983

![memcachier-ec2-config](/images/articles/memcachier-ec2-config.png)

>Note: If you are using a free dev tier, only the US East and EU West regions are available. You may want to create a Nitrous box in the same region to see the best performance.

### Connecting Your App to MemCachier

![memcachier-config](/images/articles/memcachier-config.png)

Once you have your App created, you will see a page with your configuration settings as well as getting started guides. Follow the guide which utilizes the language or framework you are building with.

### Support

All MemCachier support and runtime issues should be submitted to [Nitrous.IO](mailto:support@nitrous.io), or posted on [stackoverflow](http://www.stackoverflow.com) with the tag #nitrousio . Any non-support related issues or product feedback is welcome via email at: [support@memcachier.com](mailto:support@memcachier.com)

Any issues related to MemCachier service are reported at [MemCachier Status](http://status.memcachier.com/).

Please also follow us on twitter, [@memcachier](http://twitter.com/MemCachier), for status and product announcements.
