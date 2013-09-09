---
layout: post
title: "How to Display a Neatly Formatted Path"
date: 2013-09-08 21:43
comments: true
categories: nerdliness
link: false
---
The following function displays your `PATH` environment variable using color
coding and showing each path entry on its own line.

    path() {
      echo $PATH | tr ":" "\n" | \
        awk "{ sub(\"/usr\",   \"$fg_no_bold[green]/usr$reset_color\"); \
               sub(\"/bin\",   \"$fg_no_bold[blue]/bin$reset_color\"); \
               sub(\"/opt\",   \"$fg_no_bold[cyan]/opt$reset_color\"); \
               sub(\"/sbin\",  \"$fg_no_bold[magenta]/sbin$reset_color\"); \
               sub(\"/local\", \"$fg_no_bold[yellow]/local$reset_color\"); \
               sub(\"/.rvm\",  \"$fg_no_bold[red]/.rvm$reset_color\"); \
               print }"
    }

Here's a sample of the output:

    /Users/mark/.rvm/gems/ruby-1.9.3-p374/bin
    /Users/mark/.rvm/gems/ruby-1.9.3-p374@global/bin
    /Users/mark/.rvm/rubies/ruby-1.9.3-p374/bin
    /Users/mark/.rvm/bin
    /usr/local/bin
    /usr/bin
    /bin
    /usr/sbin
    /sbin
    /opt/X11/bin
    /usr/local/MacGPG2/bin
    /usr/local/sbin
    /Users/mark/bin

I find this function to be particularly useful when dealing with
[RVM](https://rvm.io "RVM") and [Homebrew](http://brew.sh "Homebrew") as they
are both particular about where in the `PATH` they occur.
