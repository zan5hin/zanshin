---
layout: post
title: "Recursively Find and Replace a String in All Files"
date: 2013-09-11 07:55
comments: true
categories: nerdliness
link: false
---
Using an editor it is very easy to find and replace all occurrences of a string within the file you
are editing. Some editors even make it relatively easy to find and replace a string in all files
within a project or set of files. However when the number of files grows to dozens or hundreds or
even thousands, using an editor may not be the most efficient solution.

It is very simple to accomplish the same find and replace on the command line using the Unix `find`
command coupled with the `-exec` option.

{% codeblock lang:bash %}

$ cd /path/to/directory/containing/files
$ find . -type f -exec perl -pi -e 's/source/target/g' {} \;

{% endcodeblock %}

A variation on this command would be

{% codeblock lang:bash %}

$ find . -type f -exec sed -i 's/source/target/g' {} \;

{% endcodeblock %}

You could even use `xargs` for the command.
 
{% codeblock lang:bash %}

$ find . -type f | xargs perl -pi -e 's/source/target/g'

{% endcodeblock %}

If you want to see a list of the files containing either the source or target string, you can use
this `find` command.

{% codeblock lang:bash %}

$ find . -exec grep -l "source" {} \;

{% endcodeblock %}

Read the friendly man page for `find` and `grep` for more information.

