---
layout: post
---

# Setting up a hotmail account on android with your own domain

Whenever you want to add a hotmail account to your android device, to be able to sync your email/calendar/contacs in your phone, and you have your own domain, feel free to follow this post.

For the sake of this example, lets suppose we have the domain **planetexpress.com** and our user is **bender**, hence our email address is **bender@planetexpress.com**.

Add account, and select _Microsoft Exchange ActiveSync_:

![add account]({{site.url}}/images/2013-03-12-1.png)

Add your email and password. Hit _Manual setup_:

![add email password]({{site.url}}/images/2013-03-12-2.png)

Add _Domain\User name_ and _Password_. Leave the domain part (before the backslash) blank, just put \\_user_@_domain_.  
Set _Exchange server_ to **m.hotmail.com**  
Leave _Use secure connection (SSL)_ **checked**  
Hit Next:

![add details]({{site.url}}/images/2013-03-12-3.png)

Select your desired setup:  
**Peak schedule**: how often does the application check for email in work hours (08:00 to 18:00).  
**Off-peak schedule**: how often does the application check for email outside work hours (18:00 to 08:00).  
**Period to sync email**: up to how much time in the past will the application show your emails?.  
**Emails retrieval size**: when viewing an email, this downloads the header plus the specified size.  
**Period to sync Calendar**: up to how much time in the past will the application show your calendar?.  
Hit Next:

![select setup 1]({{site.url}}/images/2013-03-12-4.png)
![select setup 2]({{site.url}}/images/2013-03-12-5.png)

Give the account a name. This does not have any effect other than helping you recognize this account among other Microsoft Exchange ActiveSync accounts.
Finally, hit Done:

![account name]({{site.url}}/images/2013-03-12-6.png)
