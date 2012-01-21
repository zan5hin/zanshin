---
layout: post
title: "Install Specific Homebrew Formula Version"
date: 2012-01-20 21:02
comments: true
categories: nerdliness
link: false
---
Earlier today, while trying to get a new [Jekyll plugin](https://github.com/tsmango/jekyll_flickr_set_tag "Jekyll FLickr plugin") to work, I was getting errors regarding **libiconv**. Without thinking about my actions I decided that I needed a newer version and so I removed it via [Homebrew](http://mxcl.github.com/homebrew/ "Homebrew").

    $ brew remove libiconv
	
And then I installed it again, 

    $ brew install libiconv
	
This fixed the problem I had getting the dependencies for the plugin to work, but it broke my Octopress installation. Badly. Whoops.

A quick search on Google turned up this [set of instructions](http://stackoverflow.com/questions/3987683/homebrew-install-specific-version-of-formula "Homebrew install specific version of formula") on Stack Overflow which fixed my problem, quickly and easily.

First you search the cache of previously installed formulae using the git command. This command assumes you are at the root of your Homebrew install, typically `/usr/local`. 

    git log -S'1.13.1' -- Library/Formula/libiconv.rb
	
In my case I previously had version 1.13.1 of libiconv and needed it back. This command will show you the commits containing that version number. There should be two, one where it was added and one where it was removed. Here are my command results:

{% codeblock %}{% raw %}
± git log -S'1.13.1' -- Library/Formula/libiconv.rb
commit b644aa151c51ea6fb0ffb69583e2e95ffca24486
Author: jmsunseri <jmsunseri@gmail.com>
Date:   Sun Aug 21 15:20:07 2011 -0500

    libiconv 1.14
    
    Signed-off-by: Jack Nagel <jacknagel@gmail.com>

commit 08c9206b03af57fa57fcc9278d83150fb38b393d
Author: Adam Vandenberg <flangy@gmail.com>
Date:   Sat Oct 30 21:35:27 2010 -0700

    Added libiconv 1.13.1
    
    libiconv with extra encodings & mac encodings.
    
    Signed-off-by: Adam Vandenberg <flangy@gmail.com>
{% endraw %}
{% endcodeblock %}

The commit I was interested in is **08c9206b03af57fa57fcc9278d83150fb38b393d**. The next commands create a branch with that commit, runs the brew install command (now against the previous version), and then return us to the master branch. The final command is option, leaving the branch in place maintains a history of what's happened.

	± git checkout -b libiconv-1.13.1 08c9206b03af57fa57fcc9278d83150fb38b393d
	Switched to a new branch 'libiconv-1.13.1'
	
	± brew install libiconv
	==> Downloading http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.13.1.tar.gz
	File already downloaded and cached to /Users/mark/Library/Caches/Homebrew
	
	± git checkout master
	Switched to branch 'master'

(The brew install libiconv output has been truncated for brevity sake.)

Now I have two versions of libiconv installed under `/usr/local/Cellar/libiconv`, 1.13.1, and 1.14. My Octopress instances are happy again, and the new plugin I am experimenting with also works. 

A momentary carelessness saved by Git. 