title: Android Application Security Part 18 - Attacking Broadcast Receivers
link: http://localhost/android-application-security-part-18/
author: exploitprotocol
description: 
post_id: 16019
created: 2015/10/13 21:52:20
created_gmt: 2015/10/13 21:52:20
comment_status: open
post_name: android-application-security-part-18
status: publish
post_type: post

# Android Application Security Part 18 - Attacking Broadcast Receivers

To get the list of exported Broadcast Receivers, you can either use drozer or can also look in AndroidManifest.xml file as i did in [Attacking Activities]() post. I will be using drozer.

![](https://i.imgur.com/hPXAX61.png)

Above is the exported broadcast receiver.

If you would see in the AndroidManifest.xml file of FourGoats application then you will find action name is **org.owasp.goatdroid.fourgoats.SOCIAL_SMS** and component name as **org.owasp.goatdroid.fourgoats.broadcastreceivers.SendSMSNowReceiver** . So we have to set these parameters in drozer accordingly.

I have also decompiled the FourGoats apk using dex2jar and opened it with Jd-Gui. Below is the snap of this particular Broadcastreceiver sourcecode.

![](https://i.imgur.com/ZgJjfxA.png)

So basically from the above code we can tell that while passing the intent we have to give two inputs "phoneNumber" and "message".

![](https://i.imgur.com/2KUyiIB.png)

The above command will try to send the messgae to the number **1234** with message **It's me Aditya**.But from Android 4.2 further control has been added on the use of SMS. Android will provide a notification if an application attempts to send SMS to a short code that uses premium services which might cause additional charges. The user can choose whether to allow the application to send the message or block it.

![](https://i.imgur.com/10v0dCv.png)

But when i modify the phoneNumber to **123456789** it will not show this confirmation dialog because Android doesn't conider that number as a Premium Number.

![](https://i.imgur.com/qDhuGwc.png)

![](https://i.imgur.com/JD2lrQy.png)

So in this way an mailicious app can take advantage of some exported BroadcastReceiver of another app.