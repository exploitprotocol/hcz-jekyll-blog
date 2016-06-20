title: Android Application Security Part 1- Setup Mobile Pentesting Platform
link: http://localhost/android-application-security-part-1/
author: exploitprotocol
description: 
post_id: 168
created: 2015/01/09 20:08:00
created_gmt: 2015/01/09 20:08:00
comment_status: open
post_name: android-application-security-part-1
status: publish
post_type: post

# Android Application Security Part 1- Setup Mobile Pentesting Platform

I think this will be the easiest blog post which i am going to write in this series because of the Awesome tool [Appie](http://manifestsecurity.com/appie/) which contains all the tools neccessary for Android Application Assessment. So you just need to [Download](manifestsecurity.com/appie/#Download) if you have not downloaded it yet. 

#### Q. That's All ?

Nope. Although [Appie](http://manifestsecurity.com/appie/) contains the most of the tools neccessary for Android Application Pentesting. But we need a Android Device assess apps. So for that we need to create an Emulated Android Device and install Genymotion for that.

  * Now, we need to Download and Setup  [Genymotion](http://www.genymotion.com/) ![](https://i.imgur.com/SwQ2Z7n.png)
  * Enter your credentials for setting up the account as given above and then after activating the account please move to the URL  <https://cloud.genymotion.com/page/launchpad/download/>  and then choose the option as given in the Image Below. ![](https://i.imgur.com/XBfT4d6.png)
  * After downloading the setup and installing on the local computer. Open settings in the Genymotion  and then after inserting your credentials which you have registered on Genymotion site. ![](https://i.imgur.com/zOIxl9U.png)
  * Click on Add.
  * Then Choose **Google Nexus 4-4.2.2** and click next. There is a reason for choosing this device with Android 4.2.2 because we will be using **Cydia Susbtrate** which can only work up to Android 4.2 ![](https://i.imgur.com/0j93r3b.png)

  * So now u have an Working Virtual Android device which is an important part in Android Pentesting. 

Now you also need to set adb path in Genymotion which is there is Appie in order to use virtual device with Appie.

  * First go to Genymotion then click on settings.
  * Then in the ADB tab, select "Use Custom Android SDK Tools"
  * Then select the path of sdk folder which is located at `path_to_appie/bin/adt/sdk/`

![](https://i.imgur.com/p0D8peg.png)

If it through an error that "AAPT tool not found". Ignore it.