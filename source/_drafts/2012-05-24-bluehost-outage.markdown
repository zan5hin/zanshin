---
layout: post
title: "Bluehost Outage"
date: 2012-05-24 15:49
comments: true
categories: nerdliness
link: false
---
Beginning about 8:15 am Tuesday morning, May 22 Bluehost suffered a major outage. Since I don't work for Bluehost, and since they are never forthcoming about their outages I can only guess as what happened by drawing inferences from the infrequent status page updates and my support chat conversations. In a nutshell all my sites were down for 16 hours, and email server was only returned this morning. Email service was interrupted once since this morning.

##Tuesday May 22, 8:15 am - 1:30 pm
I use [Mint](http://haveamint.com "Mint") as a visit tracking system and frequently have it open in one tab of my browser. I first noticed something was up when that tab said the server wasn't responding. After attempting to access my websites and my wife's websites and finding them all down I went to the [Bluehost Server Status page](https://www.bluehost.com/cgi/serverstatus/ "Bluehost Server Status"). The status message indicated that a hardware upgrade was in progress.

'''
05/22/2012 07:19am: A hardware upgrade is currently in progress. Updates may include (but are not limited to): memory, disk space, and processor. The duration of the update is approximately 30 to 60 minutes.
'''

(All status messages and chat times from Bluehost are in US Mountain Time as they are located in Utah.)

This message indicated that some kind of upgrade was in progress. I wasn't happy about an upgrade during daylight hours, but I suspect that they have international customers so it's always a bad time to upgrade servers. After an hour the time-stamp on this message was updated, but the message itself remained the same.

'''
05/22/2012 08:21am: A hardware upgrade is currently in progress. Updates may include (but are not limited to): memory, disk space, and processor. The duration of the update is approximately 30 to 60 minutes.
'''

After another hour the plot thickened as a new message appeared. 

'''
05/22/2012 09:26am: Our technician is currently investigating a server problem. The source of this problem is unknown at this time. The duration of assessing this is approximately 15 to 45 minutes.
05/22/2012 09:26am: The system files section of one of the hard drives on a shared hosting server is damaged. We need to repair the files so that we can ensure your data is preserved. Estimated time is between 30-60 minutes.
'''

This new message makes me suspect that there was either a problem with the upgrade or, in some perverse kind of irony, the hardware failed during (or as a result of) the upgrade. The second message indicated that the file system had been damaged and that they were repairing it.

Shortly after lunch when I tried to access any of my sites I was presented with a message saying that "no website was configured at this address". Something that wasn't true. I initiated the first of many support chat sessions to find out more information.

'''
Jon: [11:45:34 AM] Welcome to our real-time support chat. How can I help you today? 

Please remember that I am usually chatting with 3 or 4 users at the same time, but I will respond to you as quickly as I can.
Mark Nichols: [11:45:34 AM] While the status messages regarding this morning's outage are now gone from https://www.bluehost.com/cgi/serverstatus/, none of my sites exists any more. All that I see is a page saying there is no site configured for that address. Is there still a recovery effort under way that will restore my sites to their full, working condition? Or am I now left to restore everything?
Jon: [11:45:39 AM] How am I able to assist you today?
Mark Nichols: [11:46:04 AM] Will Bluehost be restoring my sites now that the server is working again?
Jon: [11:47:36 AM] checking now
Mark Nichols: [11:48:33 AM] I'm now missing a dozen domains and or sub-domains.
Jon: [11:49:02 AM] okay
Mark Nichols: [11:49:42 AM] Also, my mail appears to not be working
Jon: [11:50:32 AM] okay yes I have been able to confirm it that are admins are working on it trying to get it back up and running (when it comes back the sites will start working as they should
Mark Nichols: [11:50:59 AM] Any estimate on when that will happen?
[11:51:16 AM] Will I receive any kind of notice that my sties and email are working again?
Jon: [11:51:50 AM] at this time there isn't anything that will notify you (outside of the system starting to work)
Mark Nichols: [11:53:18 AM] Great. I realize that unplanned outages happen and there is nothing that can be done about that. However, my sites and email have been down since early this morning. And now there's a placeholder page that sasys there is no site configured at my domain addresses. It makes it look like *I* haven't created my site. When in fact the issue is Bluehost's fault. I am extremely dissatisfied with this experience today
Jon: [11:53:53 AM] at this time what is up due to the Apache webserver not working correctly
Mark Nichols: [11:55:55 AM] So all i can do is keep hitting refresh on my site(s) until they reappear. Will there be any communication to me if the restore efforts are unsuccessful? In other words, when do I assume that my site(s) won't be restored and that I need to restore them myself?
Jon: [11:56:39 AM] unfortunately (I would give it 15 - 20 minutes to allow some work to be done on the server)
Mark Nichols: [11:57:18 AM] It's now 12:56 pm Central time. I should expect to see my dozen sites up and running again, and have the restoration of email by 1:30 pm Central time?
Jon: [11:57:49 AM] as I said As Soon As Possible (anything else is a best guess)
Mark Nichols: [11:58:58 AM] Out of curiosity, is there any compensation for the down time?
Jon: [11:59:52 AM] that is only addressed after it is back up (You can put in a request at feedback@bluehost.com)

'''
At around 12:54 pm Central time (11:54 am Mountain time) the status message was changed again.

'''
05/22/2012 11:54am: The system files section of one of the hard drives on a shared hosting server is damaged. We need to repair the files so that we can ensure your data is preserved. Estimated time is between 30-60 minutes.
'''

At about 1:30 pm Central time I was able to see at least the home page of all of my sites. Some pages within the sites weren't yet available but we seemed to be making progress. Email still was getting rejected and I had no ssh access to the server.

By 2:30 Central I had ssh access but still no email. All the sites again appeared to be working, but were very sluggish loading.

The status page continued to be updated periodically but not in an informative way.

'''
05/22/2012 02:00pm: Our technician is currently investigating a server problem. The source of this problem is unknown at this time. The duration of assessing this is approximately 15 to 45 minutes.

05/22/2012 02:19pm: There are unexpected Server problems that the admins are currently working on. Update is needed, as so far there is no ETA.

05/22/2012 06:20pm: There are unexpected Server problems that the admins are currently working on. Update is needed, as so far there is no ETA.
'''

I had an evening chat with Bluehost support, but failed to copy that one for posterity. Th
