title: Android Application Security Part 22 - Developer Backdoor
link: http://localhost/android-application-security-part-22/
author: exploitprotocol
description: 
post_id: 16029
created: 2015/10/13 21:55:57
created_gmt: 2015/10/13 21:55:57
comment_status: open
post_name: android-application-security-part-22
status: publish
post_type: post

# Android Application Security Part 22 - Developer Backdoor

There are sometimes when developer put a backdoor to a particular application. He/She puts that because he doesn't want somebody else to access that sensitive piece of Information and sometimes that backdoor is for debugging purposes.

If you would go through **Login Activity** then you will find that there is a Backdoor. There is a Username-Password combination which turns on some Admin Options.

![](https://i.imgur.com/qkdjy10.png)

From the above image we can figure out that 

Username: **customerservice** Password: **Acc0uNTM@n@g3mEnT**

If you would login with the credentials given above then you will see a similar Interface given below.

![](https://i.imgur.com/ejvgLk1.png)