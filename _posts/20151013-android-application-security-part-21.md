title: Android Application Security Part 21 - Exploiting Debuggable Applications
link: http://localhost/android-application-security-part-21/
author: exploitprotocol
description: 
post_id: 16027
created: 2015/10/13 21:55:21
created_gmt: 2015/10/13 21:55:21
comment_status: open
post_name: android-application-security-part-21
status: publish
post_type: post

# Android Application Security Part 21 - Exploiting Debuggable Applications

Consider a situation when your mobile is stolen and it is not rooted. If an application is marked as **debuggable** then any attacker can access the application data by assuming the privileges of that application or can run arbitary code under that application permission. In the case of non-debuggable application, attacker would first need to root the device to extract any data. 

### How to check for debuggable flag ?

I will use Sieve to demonstrate this issue.

  * Decompile .apk file using apktool then open up the AndroidManifest.xml file.

  * Look for **android:debuggable** value in the AndroidManifest.xml file. ![](https://i.imgur.com/Tq59rLD.png)

Now to see which application are connected to debugging socker(@jdwp-control), type **adb jdwp** in the console. It will list the PIDs(Process Identifiers) of the applications which can be debugged. 

In order to figure out which PID belong to our application, type **adb jdwp** before running the application you wanted to test. ![](https://i.imgur.com/cdJh9jt.png)

Now again type **adb jdwp** after opening the application and you will see that there are PIDs added to last result, so among those PIDs there is one PID which belong to our application. In my case there is only one PID **3894** which is added . ![](https://i.imgur.com/sSa9OMm.png)

Now check whether or not this PID belong to this application, in case you have got more than one PID. It should output name of the application at the end of result like **com.mwr.example.sieve** in my case. ![](https://i.imgur.com/NhyE1aT.png)

Now to simply demonstrate what an debuggable application can do, i will extract data from application private directory.

Now with the help of run-as binary we can execute commands as **com.mwr.example.sieve** application. ![](https://i.imgur.com/BEMbiID.png)

**Note: Above is the shell access of my personal phone which is not rooted.**

Now you can extract the data or run an arbitary code using application permission like shown below. ![](https://i.imgur.com/1oGGsV5.png)

But if you would try to access any other directory using this method, it won't allow you because **com.mwr.example.sieve** doesn't have access to it. ![](https://i.imgur.com/9EkidSV.png)

### How To Fix

Fix is very simple, just set **android:debuggable** flag to **false** in AndroidManifest.xml of the application.