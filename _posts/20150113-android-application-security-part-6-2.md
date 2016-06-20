title: Android Application Security Part 6-Let the Fun Begin
link: http://localhost/android-application-security-part-6-2/
author: exploitprotocol
description: 
post_id: 1966
created: 2015/01/13 14:58:00
created_gmt: 2015/01/13 14:58:00
comment_status: open
post_name: android-application-security-part-6-2
status: publish
post_type: post

# Android Application Security Part 6-Let the Fun Begin

In the upcoming post i will explain the various [Top 10 Mobile Risk 2014](https://www.owasp.org/index.php/OWASP_Mobile_Security_Project#tab=Top_10_Mobile_Risks) according to [OWASP.org](http://www.owasp.org) while attacking a vulnerable android application .

I will using FourGoats App of [OWASP GoatDroid Project](https://github.com/jackMannino/OWASP-GoatDroid-Project/wiki) which is location-based social network vulnerable app and also HerdFinancial App of [OWASP Goatdroid Project](https://github.com/jackMannino/OWASP-GoatDroid-Project/wik) which is simple Banking app. OWASP GoatDroid Project is a awesome project for the ones who want to learn about Android Application Security.

Getting Started with GoadDroid Project is already their on their [Project](https://github.com/jackMannino/OWASP-GoatDroid-Project/wiki/Getting-Started) Page. But if you are using Appie then you don't need to follow the instruction written in the above page. I have already installed the GoatDroid server files on the Appie.

  * For starting the server type **goatdroid** in the Appie. ![](https://i.imgur.com/Rtn45V6.png)

  * Click "Start Web Service" in the FourGoats Tab.It will start the server.

![](https://i.imgur.com/VKp0xFJ.png)

If you would see the FourGoats server control panel, in the bottom there are several security flaws which are there in FourGoats Application.

  * Client-Side Injection
  * Server-Side Authorization Issues
  * Side Channel Information Leakage
  * Insecure Data Storage
  * Privacy Concerns
  * Insufficient Transport Layer Protection
  * Insecure IPC

We also have to setup FouGoats Application .

  * If some of the previous posts i have also shown to install Fourgoats Application in the enumlated Device. If you are not aware then please follow the [link](http://manifestsecurity.com/android-application-security-part-4/#ADBinstall)

  * Now determine the ip address of your Host Machine.

![](https://i.imgur.com/vpsg70J.png)

So Mine is 192.168.1.5

  * Open up the FourGoats Application in Emulator .

![](https://i.imgur.com/n3IAvIO.png)

  * Tap on Destination Info and Input IP Address, Port Number as 9888 and leave other field blank.

![](https://i.imgur.com/6BcSvwZ.png)

Now you can Login and interact with App.

#### Username: goatdroid

#### Password: goatdroid

![](https://i.imgur.com/uNQ59Mk.png)