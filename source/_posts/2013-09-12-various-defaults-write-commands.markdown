---
layout: post
title: "Various Defaults Write Commands"
date: 2013-09-12 08:14
comments: true
categories: nerdliness 
link: false
---
Here are a few interesting `defaults write` commands that I have applied to my Apple Macintosh
computers.

##Finder settings
{% codeblock lang:bash %}
$ defaults write com.apple.finder AppleShowAllFiles TRUE - show hidden files
{% endcodeblock %}

This command turns on the display of hidden files in the Finder. This is particularly useful when
dealing with so called "dotfiles" or configuration files that are normally hidden.

{% codeblock lang:bash %}
$ defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES 
{% endcodeblock %}

This setting causes the full path of the currently displayed directory to be shown in the title bar
of the Finder window.

##iTunes settings
{% codeblock lang:bash %}
$ defaults write com.apple.iTunes allow-half-stars -bool TRUE
{% endcodeblock %}

With this setting enabled you can click on the rating for a track in iTunes and slide until you have
a `1/2` rating. 

##Safari settings
{% codeblock lang:bash %}
$ defaults write com.apple.Safari IncludeDebugMenu 1
{% endcodeblock %}

Turns the `Debug` menu on.

{% codeblock lang:bash %}
$ defaults write com.apple.Safari TargetedClicksCreateTabs -bool TRUE
{% endcodeblock %}

Enabling this option forces all links that have a target to open in a new tab rather than in a new
window.
