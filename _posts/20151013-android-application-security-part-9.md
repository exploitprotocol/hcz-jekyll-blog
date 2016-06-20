title: Android Application Security Part 9 – Binary Protections
link: http://localhost/android-application-security-part-9/
author: exploitprotocol
description: 
post_id: 15976
created: 2015/10/13 21:36:13
created_gmt: 2015/10/13 21:36:13
comment_status: open
post_name: android-application-security-part-9
status: publish
post_type: post

# Android Application Security Part 9 – Binary Protections

Lack of Binary Protection is the last one in [OWASP Mobile Top 10 Risk](https://www.owasp.org/index.php/Mobile_Top_10_2014-M10)

Android Application are delivered through an **.apk** file format which an adversary can reverse engineer it and can see all the code contained in it. Below are scenarios of reverse engineering an application:- 

  * Adversary can analyze and determine which defensive measure are implemented in the app and also find a way to bypass those mechanism. 
  * Also adversary can also insert the malicious code, recompile it and deliver to normal users.
  * For example, gaming apps which have some feature unlocked are widely downloaded by youngster through insecure sources(sometimes through Google PlayStore as well). Most of those modified apps contains malware and some contain advertising to gain profit from those users.

An adversary is the only **threat agent** in this case.

Below is the demostration of reverse engineering an app.

  * I will use Sieve app for demonstration.

  * First use **dex2jar** to convert **.apk** file in to **.jar** file. ![](https://i.imgur.com/JuSUi7p.png)

  * Open up the jar file in **jdgui** ![](https://i.imgur.com/4rjTQUN.png)

If you followed the above steps, you will be able to see the code of Sieve App.

### How To Fix

Application Code can be obfuscated with the help of [Proguard](https://developer.android.com/tools/help/proguard.html) but it is only able to slow down the adversary from reverse engineering android application, obfuscation doesn't prevent reverse engineering. You can learn more about proguard [here](https://developer.android.com/tools/help/proguard.html).

For security conscious application's application, [Dexguard](http://www.saikoa.com/dexguard) can be used. Dexguard is a commercial version of Proguard. Besides encrypting classes, strings, native libraries, it also adds tamper detection to let your application react accordingly if a hacker has tried to modify it or is accessing it illegitimately.