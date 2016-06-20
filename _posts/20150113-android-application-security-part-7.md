title: Android Application Security Part 7-Understanding AndroidManifest.xml File
link: http://localhost/android-application-security-part-7/
author: exploitprotocol
description: 
post_id: 2016
created: 2015/01/13 16:43:00
created_gmt: 2015/01/13 16:43:00
comment_status: open
post_name: android-application-security-part-7
status: publish
post_type: post

# Android Application Security Part 7-Understanding AndroidManifest.xml File

AndroidManifest.xml is very important part of an APK file espically when security is concerned. Every service,ContentProvider,activity,Broadcast Receiver need to be mentioned in the AndroidManifest.xml file. Let's learn more about AndroidManifest file in a short while. First i would like to tell several important methods to view decompiled AndroidManifest.xml file. 

### Method 1 - By Drozer

Drozer has a module named as **app.package.manifest** which get's the application androidmanifest.xml file and display in the drozer console. **run app.package.manifest org.owasp.goatdroid.fourgoats** will produce the output given below. 

### Method 2 - Using apktool to decompile the APK

**apktool d "OWASP GoatDroid- FourGoats Android App.apk"** will decompile the following apk file of FourGoats Application. ![](https://i.imgur.com/iNMXoDe.png) Now you can simply access the AndroidManifest.xml file from the newly folder created in the same directory in which you executed this command. 

### Method 3 - Using Androguard

I am using AndroGuard Plugin in the Sublime Text editor ,it make whole process lot simpler as compared to handling androguard files. Below is the animation depicting the process. ![](https://i.imgur.com/ZyDJD9P.gif) I would advise to stick with the Method-1 as others have limited use .I am not denying the fact that apktool and AndroGuard are also good tools but not fit for this purpose. In Android a component is public when **exported** is set to **true** but a component is also public if the manifest specifies an Intent filter for it. However, developers can explicitly make components private (regardless of any intent filters) by setting the “exported” attribute to false for each component in the manifest file. Developers can set the “permission” attribute to require a certain permission to access each component, thereby restricting access to the component.  Hope that i was successful in explaining the AndroidManifest.xml file :)