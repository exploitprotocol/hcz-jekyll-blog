title: Android Application Security Part 10 - Insufficient Transport Layer Protection
link: http://localhost/android-application-security-part-10/
author: exploitprotocol
description: 
post_id: 15983
created: 2015/10/13 21:38:24
created_gmt: 2015/10/13 21:38:24
comment_status: open
post_name: android-application-security-part-10
status: publish
post_type: post

# Android Application Security Part 10 - Insufficient Transport Layer Protection

Insufficient Transport Layer Protection holds **3rd** position at [OWASP Mobile Top 10](https://www.owasp.org/index.php/Mobile_Top_10_2014-M3).

Nearly all Android Applications transmit data between Client and Server. Most Application prefer to send data over Secure Channel to prevent interception and leaking to an malicious user. In this post i will try to highlight some issues regarding Insecure Transmission of data and ways to exploit those issue and also ways to fix them as well.

Common Scenarios

  * **Lack of Certificate Inspection:** Android Application fails to verify the identity of the certificate presented to it. Most of the application ignore the warnings and accept any self-signed certificate presented. Some Application instead pass the traffic through an HTTP connection.

  * **Weak Handshake Negotiation:** Application and server perform an SSL/TLS handshake but use an insecure cipher suite which is vulnerable to MITM attacks. So any attacker can easily decrypt that connection.

  * **Privacy Information Leakage:** Most of the times it happens that Applications do authentication through a secure channel but rest all connection through non-secure channel. That doesn’t add to security of application because rest sensitive data like session cookie or user data can be intercepted by an malicious user.

**Who are threat agents in this case ?**

  * Users local to your network (compromised or monitored wifi)
  * Carrier or network devices (routers, cell towers, proxy’s, etc)
  * Malware pre-existing on your phone
  * Hackers trying to attack you web services

For our demonstration purpose we will use HerdFinacial App from OWASP-Goatdroid Project.

  * First set the destination Info in HerdFinancial App. ![](https://i.imgur.com/Lhm0H5G.png)

  * Now we to set a proxy in our android device/emulator to intercept the traffic between application and the server. If you are using Genymotion then go to Wifi under Settings. Tap WiredSSID for a While and then tap on Modify Network. ![](https://i.imgur.com/ke7mCGZ.png)

  * In proxy settings, choose manual then enter IP Address and port on which Burp Suite or OWASP Zap is listening. ![](https://i.imgur.com/h0ae1NP.png)

  * Now device traffic can be intercepted by Burp Suite or OWASP Zap. ![](https://i.imgur.com/uoMwqJl.png) ![](https://i.imgur.com/7zifG08.png)

But if would now try open other apps like Google Play Store or Facebook App then you will not be able to see any of the traffic there. So might be wondering why is that happening. There are some possible reasons for that which are listed below :

  * Burp Generate a self-signed certificate for every host(like google.com), some application do not trasmit any data through it. Like in the above example Android Application trasmitted the data to a self signed certificate which lead to interception of data , this is worst case scenario where an android application accepts all certificates presented to it.

  * To prevent above scenario, some application uses Certificate Pinning. 

**What is certificate Pinning?**

By default, when making an SSL connection, the client(android app) checks that the server’s certificate has a verifiable chain of trust back to a trusted (root) certificate and matches the requested hostname. This lead to problem of **Man in the Middle Attacks(MITM)**. In certificate Pinnning, an Android Application itself contains the certificate of server and only transmit data if the same certificate is presented.

  * There are some rare application which uses custom protocols instead of HTTP/HTTPS to transmit data. Either because of requirement or because to prevent interception through common techniques.

  * There are some ultra rare application’s which also encrpyts data before placing data in HTTP Request Body, which ultimately then passed through an SSL connection to the server.

Facebook and other security conscious applications applies certificate Pinning and encryption of HTTP(s) Request body as well.

Below we will try to understand how to actually intercept traffic when those above limitations are there.

**First Scenario**

  * Security in Settings have an option to view to all Trusted Certificates installed on the device.

  * In order to Bypass first scenario where application only trust certificates from list of Trusted CA’s. We need to add Burp Certificate in Trusted CA Certificates.

  * Go to the Browser and type http://burp . It will open a webpage, choose CA Certificate from there. It will download certificate for you will appear in notification. ![](https://i.imgur.com/BrVvjNd.png) ![](https://i.imgur.com/ixyJY22.png)

  * Now open File Manager Application and then open up Download folder within it. You will find the file, click on it and enter Burp when asked for name. ![](https://i.imgur.com/zRPpI6I.png) ![](https://i.imgur.com/toySWlN.png)

  * Now if you would go to list og Trusted CA Certificates in Settings–>Security–>Trusted Credentials. You Will find the PortsWigger CA Certificate is installed. ![](https://i.imgur.com/JeKOFwf.png)

So finally after all this we have finally installed a trusted CA certificate. Now this will help in intercepting in most of the applications.

**Second Scenario**

There are two bypass Certificate Pinning, first by changing the source code and other by Android-SSL-Trust-Killer. Changing source code is always a tedious Job, because every Application has it's own implementation of Encryption.

We would instead take a simpler path for now, will install [Android SSL-Trust-Killer](https://github.com/iSECPartners/Android-SSL-TrustKiller) application in the android device which will bypass SSL Certificate Pinning for nearly all application.

  * Make Sure [Cydia Substrate](http://www.cydiasubstrate.com/download/com.saurik.substrate.apk) is installed on the device/emulator.

  * Download Android SSL-Trust-killer from [here](https://github.com/iSECPartners/Android-SSL-TrustKiller/releases/download/v1/Android-SSL-TrustKiller.apk).

  * Install using **adb install Android-SSL-TrustKiller.apk**

  * Restart the device/emulator using Cydia Substrate. Now if you try to intercept then you can see most of traffic from nearly every app in BurpSuite . ![](https://i.imgur.com/CfZFfhS.png)

Now if you would see the Request/Response in BurpSuite, you will find some traffic in which Body part of the request is not readible. Like the request given below which was originated from **Android Gmail App**. ![](https://i.imgur.com/PNmJ54w.png) So in this actually all the data was encrypted before it was placed in the Body of Request. In such kind of situation, we cannot do anything because this layer of encryption cannot be broken.

### How To Fix

  * Apply SSL/TLS to transport channels that the mobile app will use to transmit sensitive information, session tokens, or other sensitive data to a backend API or web service.
  * Use strong, industry standard cipher suites with appropriate key lengths.
  * Use certificates signed by a trusted CA provider and consider certificate pinning for security conscious applications.
  * Alert users through the UI if the mobile app detects an invalid certificate.