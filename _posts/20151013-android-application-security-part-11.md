title: Android Application Security Part 11 - Unintended Data Leakage
link: http://localhost/android-application-security-part-11/
author: exploitprotocol
description: 
post_id: 15989
created: 2015/10/13 21:41:28
created_gmt: 2015/10/13 21:41:28
comment_status: open
post_name: android-application-security-part-11
status: publish
post_type: post

# Android Application Security Part 11 - Unintended Data Leakage

Unintended Data Leakage holds **4th** position at [OWASP Mobile Top 10](https://www.owasp.org/index.php/Mobile_Top_10_2014-M4)

As the name suggest "Unintended Data Leakage" means when developer of the application accidently leaks the data. Well any developer would never want to leak the data but in some scenarios he assumes that the particular data is only accessible to the application not to any adversary. Below are some of the example scenarios.

### Threat Agents

  * Malware Apps

  * adversary who has physical access to device

### Logging

Often Developers leave debugging information publicly. So any application with READ_LOGS permission can access those logs and can gain sensitive information throught that.

If will use Sieve Application to demonstrate this issue.

  * Type **pidcat com.mwr.example.sieve** in Appie. [Pidcat](https://github.com/JakeWharton/pidcat) is a modified version of logcat with better viewing of logs.
  * Now open up Sieve Application and enter your password. ![](https://i.imgur.com/Tih6hlI.png)
  * Now you will notice that your password is seen in pidcat when you entered it in Sieve. As in the picture below , my password is displayed which is **1234567890123456** ![](https://i.imgur.com/Ylx9280.png)

* * *

#### Copy/Paste Buffer Caching

Android provides clipboard-based framework to provide copy-paste function in android applications. But this creates serious issue when some other application can access the clipboard which contain some sensitive data. 

**How To Fix**

Disable copy/paste function for sensitive part of the application. For example, disable copying credit card details.

* * *

### Crash Logs

If an application crashes during runtime and it saves logs somewhere then those logs can be of help to an attacker especially in cases when android application cannot be reverse engineered.

**How To Fix**

Avoid creating logs when applications crashes and if logs are sent over the network then ensure that they are sent over an SSL channel.

* * *

### Analytics Data Sent To 3rd Parties

Most of the application uses other services in their application like Google Adsense but sometimes they leak some sensitive data or the data which is not required to sent to that service. This may happen because of the developer not implementing feature properly.

You can look by intercepting the traffic of the application and see whether any sensitive data is sent to 3rd parties or not. 

### Reference

[OWASP Mobile Top 10 M4](https://www.owasp.org/index.php/Mobile_Top_10_2014-M4)