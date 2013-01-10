---
layout: post
title: "How to Update a Github Fork"
date: 2013-01-10 17:27
comments: true
categories: nerdliness
link: false
---
Once upon a time you found a project on Github that caught your fancy and you made a fork of your very own. You made some changes and time passed. Now you realize that the original project has some new features you want in your fork. What to do?

##Step 1
Add a `remote` to the original, or upstream project.

{% codeblock lang:bash %}
$ git remote add upstream git://github.com/originalOwner/project.git
{% endcodeblock %}

You can confirm the remote with this command:

{% codeblock lang:bash %}
$ git remote -v
{% endcodeblock %}

There will (at least) be a pair of references to `origin` (your fork of the project) and a pair of references to `upstream`, the new remote you've added for the upstream project.

##Step 2
Fetch all the changes from the upstream project. This will gather all the branches of that upstream project.

{% codeblock lang:bash %}
$ git fetch upstream
{% endcodeblock %}

##Step 3
Make sure you are on the master branch of your local repository:

{% codeblock lang:bash %}
$ git checkout master
{% endcodeblock %}

##Step 4
Rebase your branch so that any changes you've made which aren't in the upstream repository are replayed, thus preventing you from losing them.

{% codeblock lang:bash %}
$ git rebase upstream/master
{% endcodeblock %}

##Step 5
Push your newly updated local repository to your Github fork. You may need to add the `-f` flag to force the push on the initial push after a rebase.

{% codeblock lang:bash %}
$ git push [-f] origin master
{% endcodeblock %}
