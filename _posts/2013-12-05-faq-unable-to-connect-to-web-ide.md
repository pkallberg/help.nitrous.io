---
layout: article
title: Unable to connect to Web IDE
published: true
categories: [faq, web ide]
---

If you're running into the issue where the message "connecting..." displays at the top of the web IDE, you may be experiencing a network or firewall related issue.

To be able to connect to the web IDE you will need to ensure port 443 is open, and also that your network is not blocking WebSockets. Test your browser at [WebSocket.org](http://www.websocket.org/echo.html) to ensure your network isn't blocking WebSockets.

If you do not have port 443 or WebSockets enabled then you will need to contact your network administrator in regards to making adjustments.
