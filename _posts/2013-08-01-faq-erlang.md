---
layout: article
title: Installing Erlang
published: true
categories: [faq]
---

Although the Nitrous boxes include a number of [interpreters and tools](/box-interpreters-and-tools/), we don't have everything covered. Fortunately many languages can be installed (Clojure, Dart, Haskell, Erlang, Scala, etc). This guide will cover how to setup your box to support Erlang.

### Downloading Erlang

Since you can't create folders outside your home folder, you will need to install Erlang within it. Create a hidden folder called .tools:

    mkdir ~/.tools

Navigate to this new directory and download Erlang:

    cd ~/.tools

    wget https://elearning.erlang-solutions.com/binaries/sources/otp_src_R16B01.tar.gz

>Note: Other versions of Erlang may be found on [erlang-solutions.com](https://www.erlang-solutions.com/downloads/download-erlang-otp)

Now you will want to extract this file which will create the folder `otp_src_R16B01/` inside.

    gunzip -c otp_src_R16B01.tar.gz | tar xfp -

### Setting up PATH

Once the tar file is extracted, edit `~/.bashrc` and add the bin directory to your PATH:

    PATH=$PATH:$HOME/.tools/otp_src_R16B01/bin/

Reload the ~/.bashrc file by running `source ~/.bashrc`, and verify the .tools folder was added to your PATH with `echo $PATH`.

### Installing

Navigate to the Erlang directory `cd ~/.tools/otp_src_R16B01/` and run the following command:

    ./configure

Next, run make (this can take a few minutes):

    make

Once finished you should have a working Erlang/OTP system. You can try this out by typing `bin/erl`.