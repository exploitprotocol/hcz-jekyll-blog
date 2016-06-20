title: Android Application Security Part 5 - Starting Drozer
link: http://localhost/android-application-security-part-5/
author: exploitprotocol
description: 
post_id: 2019
created: 2015/01/13 13:15:01
created_gmt: 2015/01/13 13:15:01
comment_status: open
post_name: android-application-security-part-5
status: publish
post_type: post

# Android Application Security Part 5 - Starting Drozer

In this post i will be demonstrating [Drozer](https://www.mwrinfosecurity.com/products/drozer/) which is one of the essential tool in Android Application Security Assessment. It reduces the time involved in App Security Assessment.

Drozer is already installed in the Appie, if you using it then no need of installation and setup procedure. 

  * First open up the Appie and the Genymotion Device.

  * Download [Drozer App](https://www.mwrinfosecurity.com/system/assets/614/original/agent.apk)

  * Open the drozer application in running emulator and click the **OFF** button in the bottom of the app which will start a Embedded Server. ![](https://i.imgur.com/u06mkxu.png)

  * By default the server is listening on Port Number 31415 so in order to forward all commands of drozer client to drozer server we will use Android Debug Bridge[ADB] to forward the connections.

Type **adb forward tcp:31415 tcp:31415** in the console.

  * Type **drozer console connect** and it will spilt the screen and open the drozer in the other part. ![](https://i.imgur.com/wWdCCRC.png)

The above steps are needed to be done whenever we need to perform assessment through Drozer.

Now you can just type on **list** in the drozer console and it will list all the modules which came pre-installed with Drozer .

![](https://i.imgur.com/0Ro036x.png) ![](https://i.imgur.com/hVTES7r.png) ![](https://i.imgur.com/PWyt5np.png)

You can use **\--help** switch with any of module given above to get to know more about the functionality of that particular module

For example **run app.package.info --help** will output

![](https://i.imgur.com/UbkcV4j.png) ![](https://i.imgur.com/wtLqcXV.png)

I will be describing most of the Drozer modules while exploiting vulnerable apps in the upcoming posts.

## Comments

**[Maluko](#11 "2015-02-06 22:35:00"):** I'm having issues when using drozer. When I do list nothing comes up. Any ideas?

**[Aditya Agrawal](#12 "2015-02-07 04:38:00"):** Ok. That's unexpected.Did other modules worked like app.package.info ? May be you should try restarting Appie and Genymotion Device. If that doesn't solve that problem , please let me know.

