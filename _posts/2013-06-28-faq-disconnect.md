---
layout: article
title: Server disconnects on browser close
published: true
categories: [faq, web-ide]
---

If you're running a server or long-running process that you don't want to interrupt when you mistakenly close your browser window, we suggest using a terminal multiplexer like [screen](http://www.gnu.org/software/screen/) or [tmux](http://tmux.sourceforge.net/) and creating a persistent session to which you can reconnect.

We pre-install tmux on all boxes, so you're ready to go out of the gate. You can access tmux via the terminal in [the Web IDE](ide-general#console) or by [SSHing into your box](/categories/ssh).

### Getting started with tmux

At it's core, tmux is made of *sessions* which contain any number of *windows* which can be split into *panes*. That's pretty much it.

**Create a new Session**

In a Web IDE console window, you can create a new tmux session named "my_session" like so:

    tmux new -s my_session

**List sessions**

    tmux ls

**Attach to a session**

    tmux attach -t my_session

**Detach a session**

    tmux detach

**Create window**

    tmux new-window


### Navigating tmux

The exact key bindings will depend on your operating system and keyboard setup. To see the current key bindings, type:

    tmux list-keys

To get a list of tmux commands:

    tmux list-commands

<p class="alert">
Note that navigating in tmux will take a bit of time to master. Switching windows and creating different pane layouts isn't as easy as dragging windows in a GUI so you'll want to customize your tmux configuration file (~/.tmux.conf).
</p>