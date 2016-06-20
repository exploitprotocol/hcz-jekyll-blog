title: Android Application Security Part 17 - Attacking Activities
link: http://localhost/android-application-security-part-17/
author: exploitprotocol
description: 
post_id: 16017
created: 2015/10/13 21:51:25
created_gmt: 2015/10/13 21:51:25
comment_status: open
post_name: android-application-security-part-17
status: publish
post_type: post

# Android Application Security Part 17 - Attacking Activities

As i have defined in [Android Application Security Part 3 - Android Application Fundamentals](https://manifestsecurity.com/android-application-security-part-3/), an activity is a graphical user interface of an application for the user. An application mostly have more than one activity. Each activity is different, for example activity for login of an application is different and for changing settings is different. 

You can use Drozer to find all the activities in an application or you could also see the listed activities in AndroidManifest.xml file.

![](http://i.imgur.com/80suO2M.png)

If the appplication is not obfuscated then you can reverse engineer it and see it source code. ![](http://i.imgur.com/Kxz9gks.png) ![](https://i.imgur.com/80EtckG.png)

**Note: It is not necessary that you will see activities listed like above in case of other application. That is dependent on developer of the application.**

### Exported Activities

Exported Activities are those activities which can be accessed by other application on the same device. Most of the time after authentication on an Android Application, it shift to a new activity which basically users are aware off(like music playlist after your music player login). But developers keep those activities exported and even without custom permissions.

  * If you would see in the HerdFinancial Application then you will find that **org.owasp.goatdroid.herdfinancial.activities.Main** is exported and also it doesn't even have any custom permissions.

  * You can simply pass an intent through Drozer to start that particular activity. ![](https://i.imgur.com/CqQbeyn.png)

  * After that you will see that Herfinancial Application has been started with default account i.e with the account number **1234567890** and now you can do sort of stuff like transfer the money to someone else account. How scary it would be if something like this exist for our Banking apps! ![](https://i.imgur.com/SQ0Z4LX.png)

If you are an android developer then you can also make a proof of concept application to demonstrate this behaviour.