title: Android Application Security Part 13 - Broken Cryptography
link: http://localhost/android-application-security-part-13/
author: exploitprotocol
description: 
post_id: 16007
created: 2015/10/13 21:46:49
created_gmt: 2015/10/13 21:46:49
comment_status: open
post_name: android-application-security-part-13
status: publish
post_type: post

# Android Application Security Part 13 - Broken Cryptography

In this post i will be talking about Broken Cryptography. As per OWASP-Mobile Security Project **Broken Cryptography** is on the 6th position. In this post i will be talking about certain vulnerabilities which are created by implenting either insecure cryptographic implementation or by implementing in a insecure way.

So according to OWASP below are the scenarios which can occur in an application

  * Poor Key Management Processes
  * Creation and Use of Custom Encryption Protocols
  * Use of Insecure and/or Depcreated algorithms.

### Poor Key Management Processes

The best encryption doesn't matter when you do not handle keys properly.Below are some scenarios which are common in Application building:-

  * Including the keys in the same attacker-readable directory as the encrypted content
  * Making the keys otherwise available to the attacker
  * Avoid the use of hardcoded keys within your binary

For demonstrating following scenario we will use HerdFinancial App from the OWASP Goatdroid Project from which we have used Fourgoats Application in the earlier demonstration. You can download HerdFinancial Application from [here](http://sourceforge.net/projects/appiefiles/files/OWASP%20GoatDroid-%20Herd%20Financial%20Android%20App.apk/download)

  * Convert HerdFinancial .apk file using dex2jar ![](https://i.imgur.com/gKCKkxj.png)

  * Now open that .jar file in Jg-Gui and open up the StatmentDBHelper class as shown below. ![](https://i.imgur.com/vjXgdjN.png)

  * Similarly you can open UserInfoDBHelper class   
![](https://i.imgur.com/fB5HdBA.png)

You can see above that password for encrypting db files are stored in HerdFinancial Application. Passwords are **hammer** and **havey0us33nb@seball** . So anyone with HerdFinancial Application can get password using reverse engineering and then decrypt the content using those keys.

Let's us decrypt files which were created by HerdFinancial App

### Creation and Use of Custom Encryption Protocols

Most of the time Application developers create and use their own Encryption Algorithms or Protocols, which utlimately create new vulnerabilities.

While developers have some valid reasons for using Custom Encryption Algortihms/Protocols like default SSL Libraries are not that fast and efficient for their purpose.

There is a Awesome library **[Conceal](https://github.com/facebook/conceal)** which was developed by Facebook suitable for Applications wanted to Encrypt large files in an efficient manner.

### Use of Insecure and/or Deprecated Algorithms

Many of the application uses Insecure/Deprecated Algortithms which were proven vulnerable to various attacks and should not be used any longer if want support cryptography in the application.Some of the them are listed below:

  * RC4
  * MD4
  * MD5
  * SHA1

#### Reference

[OWASP Top 10 2014 - M6](https://www.owasp.org/index.php/Mobile_Top_10_2014-M6)