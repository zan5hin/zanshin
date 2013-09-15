---
layout: post
title: "How to Delete Your Quarantine Download History"
date: 2013-09-13 23:14
comments: true
categories: nerdliness
link: false
---
On Mas OS X, Launch Services keeps a list of everything you've ever downloaded. Launch services
quarantine is what triggers the warning about opening files downloaded from the Internet,
consequently it has a list of everything you've downloaded.

This command will list all the files in your quarantine list.

{% codeblock lang:bash %}
sqlite3 ~/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV* 'select LSQuarantineDataURLString from LSQuarantineEvent'
{% endcodeblock %}

You should see something that ends up looking like this.

{% img /images/quarantine.png %}

You can also append `| sort` to the end of the command to sort the output. And if you are confident with SQL you can write more advanced queries to explore your download history.

To clear your history run this command.

{% codeblock lang:bash %}
sqlite3 ~/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV* 'select LSQuarantineDataURLString from LSQuarantineEvent'
{% endcodeblock %}


