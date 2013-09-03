---
layout: post
title: "How to Use Homebrew Zsh Instead of Mac OS X Default"
date: 2013-09-03 08:42
comments: true
categories: nerdliness
link: false
---
Out of the box Mac OS X version 10.8.x (Lion) comes with zsh version 4.3.11 (i386-apple-darwin12.0). However zsh is currently at version 5.0.2 (x86_64-apple-darwin12.2.1). Here's how to use the newer version.

Install zsh using [Homebrew](http://brew.sh "Homebrew").

    $ brew install zsh

Edit `/etc/shells` to add a new entry for the Homebrew zsh.

    $ sudo vim /etc/shells

The resulting `/etc/shells` file should look like this:

    /bin/bash
    /bin/csh
    /bin/sh
    /bin/tcsh
    /bin/zsh
    /usr/local/bin/zsh

The `/usr/local/bin/zsh` location is the symlink Homebrew creates when installing zsh.

To actually change the shell assigned to your user account run

    $ chsh -s /usr/local/bin/zsh

Now you have the most recent zsh as your shell. 
