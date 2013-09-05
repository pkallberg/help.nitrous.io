---
layout: article
title: Changing Python versions with virtualenv
published: true
categories: [faq]
---

The Python/Django box template comes pre-installed with virtualenv and many versions of python.

To see which versions of Python are available on your box, run the following command:

    ls /usr/bin/python*

This will provide you with a list of python versions available. You will notice that `/usr/bin/python3.3` is listed for Python 3.3, and you can create an isolated environment with this version by running the following command:

    virtualenv -p /usr/bin/python3.3 py3env

Next, type in the following command to start working in this environment:

    source py3env/bin/activate
