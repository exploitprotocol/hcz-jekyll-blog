title: Android Application Security Part 4-Get to know about your Arsenals
link: http://localhost/android-application-security-part-4/
author: exploitprotocol
description: 
post_id: 245
created: 2015/01/10 20:08:00
created_gmt: 2015/01/10 20:08:00
comment_status: open
post_name: android-application-security-part-4
status: publish
post_type: post

# Android Application Security Part 4-Get to know about your Arsenals

For all the demos below i have used FourGoats Application from [OWASP-Goatdroid-Project](https://github.com/jackMannino/OWASP-GoatDroid-Project). You can download from [here](http://sourceforge.net/projects/appiefiles/files/OWASP%20GoatDroid-%20FourGoats%20Android%20App.apk/download)

### Android Debug Bridge

Below i have described must know methods of adb but i would recommend you to go through [ADB Documentation](https://developer.android.com/tools/help/adb.html) to gain a better understanding of it.

  * adb devices - It Prints a list of all attached emulator/device instances.![](https://i.imgur.com/FGOArow.png)
  * adb install

\- It is used to install an apk file in to an Emulated/Connected Device. We will be pushing apk which we have downloaded above.![](https://i.imgur.com/RcpvHLs.png)
  * adb pull - It is used to fetch some data from Emulated device(remote) to local host(local). ![](https://i.imgur.com/6LuBHUQ.png)
  * adb push - It is used to push some data from local host(local) to Emulated Device(remote).Similarly we can also push file to the device.![](https://i.imgur.com/HTftZH4.png)
  * adb forward - Forwards socket connections from a specified local port to a specified remote port on the emulator/device instance.![](https://i.imgur.com/AltyWY2.png)
  * adb shell - Adb provides a Unix shell that you can use to run a variety of commands on an emulator or connected device. ![](https://i.imgur.com/PizWhrP.png)

Although there are some other utilities, Activity Manager(am) and Package Manager(pm) in adb shell. But we will use drozer for the same commands just because drozer offers to do task simply.

### Drozer

Drozer allows you to search for security vulnerabilities in apps and devices **by assuming the role of an app** and interacting with the Dalvik VM, other apps’ Inter Process Communication(IPC) endpoints and the underlying OS.

As Drozer is a very important tool in Android Application Security Assessment, i have written a seperate post for it.

> [Android Application Security Part 5- Firing Drozer](http://manifestsecurity.com/android-application-security-part-5/)

### Apktool Usage

  * Type **apktool** in the Appie and it will list the default options of apktool.![](https://i.imgur.com/OiOurWs.png)
  * Mainly we will be decoding an APK file for that we need to run **apktool d filename.apk**. After running that , it will create a folder in the same directory with decompiled files in it.![](https://i.imgur.com/8ZaOnSB.png)

### dex2jar Usage

  * dex2jar is mainly used to convert an APK file in to a jar file containing reconstructed source code. **dex2jar filename.apk** command will convert the APK file in to a jar file.![](https://i.imgur.com/4SkwtRB.png)

### JD-GUI Usage

  * Above we have converted the APK file in to a jar file.

  * Now you can open that jar file in JD-GUI and view that reconstructed source code.

  * First type **jdgui** in Appie,it will open JD-GUI within the Appie. ![](https://i.imgur.com/1MwnPt4.png)
  * Then open up the jar file in JD-GUI.![](https://i.imgur.com/BgnHz4b.png)

## Comments

**[todaro](#9 "2015-02-05 05:57:00"):** i have a question：how can i go into d:project ?，now i am in C:UserstodaroDesktopapp，thx，email or just reply here。another，my english is poor，so。。。。

**[Aditya Agrawal](#10 "2015-02-05 06:34:00"):** Just type "D:" without quotes in the console, it will take to D drive then type "cd project" to move in the following folder. Not a problem, i am able to understand your english :)

