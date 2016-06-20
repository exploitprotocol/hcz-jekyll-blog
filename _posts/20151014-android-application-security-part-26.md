title: Android Application Security Part 26 - Intercept Traffic on Android version after 4.2.2
link: http://localhost/android-application-security-part-26/
author: exploitprotocol
description: 
post_id: 16210
created: 2015/10/14 15:02:50
created_gmt: 2015/10/14 15:02:50
comment_status: open
post_name: android-application-security-part-26
status: publish
post_type: post

# Android Application Security Part 26 - Intercept Traffic on Android version after 4.2.2

In this post i will demonstrate to intercept traffic after Android 4.2.2. Most of the android security professionals uses [Cydia Substrate](http://www.cydiasubstrate.com/) and [Android-SSL-TrustKiller](https://github.com/iSECPartners/Android-SSL-TrustKiller) for intercepting traffic but as [Cydia Substrate](http://www.cydiasubstrate.com/) is not supported after Android 4.2.2 , it may be a problem to some users who want to pentest app which only works on Kitkat(Android 4.4.4) or Lollipop(Android 5.0.0) .

So i will be using a [Xposed Framework](http://repo.xposed.info/module/de.robv.android.xposed.installer) and [JustTrustMe](https://github.com/Fuzion24/JustTrustMe) which is an xposed framework module.

  * First download Xposed Installer apk from [here](http://repo.xposed.info/module/de.robv.android.xposed.installer) and install on your device.

  * Now download JustTrustMe apk from [here](https://github.com/Fuzion24/JustTrustMe/blob/master/bin/JustTrustMe.apk?raw=true) and install it on your device.

  * Then open up your Xposed Installer App from your device and open modules in it. Then click on the checkbox to activate that module. ![](https://i.imgur.com/8XHS4kB.png)

  * Now go to the framework section and choose **Soft Reboot** to reboot and activate that module. ![](https://i.imgur.com/GBaBMag.png)

Now if you would try to intercept using your Burp Proxy then you would be able to see the traffic of every apps.