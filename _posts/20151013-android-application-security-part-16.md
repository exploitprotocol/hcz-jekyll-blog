title: Android Application Security Part 16 - Attacking Services
link: http://localhost/android-application-security-part-16/
author: exploitprotocol
description: 
post_id: 16015
created: 2015/10/13 21:50:37
created_gmt: 2015/10/13 21:50:37
comment_status: open
post_name: android-application-security-part-16
status: publish
post_type: post

# Android Application Security Part 16 - Attacking Services

I have already described about Content Providers in [Android Application Security Part 3- Android Application Fundamentals](https://manifestsecurity.com/android-application-security-part-3/), please go through it if you haven’t yet.

To determine exported services, i will be using drozer.

![](https://i.imgur.com/JBNq0WF.png)

So from the above we can see that there is an **org.owasp.fourgoats.goatdroid.LocationService** service which is exported and doesn't need any Permission. So it means that any malicious app which is installed on the device with the FourGoats App can access the location of the device.**That's Dangerous**

Let's us try to Start particular Service

Below is the screenshot before i do not start the service.

![](https://i.imgur.com/DJzN50B.png)

Now i ran the following commmand

![](https://i.imgur.com/4ag05Sy.png)

And observe that location sign in the status bar and GPS location is being accessed by FourGoats app.

![](https://i.imgur.com/AbxjY1A.png)