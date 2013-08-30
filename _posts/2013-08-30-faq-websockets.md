---
layout: article
title: Using WebSockets
published: true
categories: [faq]
---

WebSockets are currently blocked on Nitrous boxes. If you are wanting to use websockets then you will want to SSH from your local machine and setup tunneling to whichever port you wish to use (we have ports 3000-9000 open).

To setup ssh tunneling you will want to run the following command in your local terminal, replacing the necessary variables:

ssh -N -p `box_port` action@`box_host` -L `local_port`/localhost/`remote_port`
