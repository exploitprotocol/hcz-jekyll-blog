title: Android Application Security Part 20 - Client Side Injections
link: http://localhost/android-application-security-part-20/
author: exploitprotocol
description: 
post_id: 16025
created: 2015/10/13 21:55:07
created_gmt: 2015/10/13 21:55:07
comment_status: open
post_name: android-application-security-part-20
status: publish
post_type: post

# Android Application Security Part 20 - Client Side Injections

Client Side Injections holds **7th** position in [OWASP Mobile Top 10](https://www.owasp.org/index.php/Mobile_Top_10_2014-M7)

  * **Javascript Injection:** The mobile browser is vulnerable to javascript injection as well. Android default **Browser** has also access to mobile applications cookies. If you have your Google account attached to device then you can use your Google account in Android Browser without authentication.

  * Several application interfaces or language functions can accept data and can be fuzzed to make applications crash. While most of these flaws do not lead to overflows because of the phone’s platforms being managed code, there have been several that have been used as a “userland” exploit in an exploit chain aimed at rooting or jailbreaking devices.

  * Mobile malware or other malicious apps may perform a binary attack against the presentation layer (HTML, JavaScript, Cascading Style Sheets ) or the actual binary of the mobile app's executable. These code injections are executed either by the mobile app's framework or the binary itself at run-time.

### How To Fix

  * **SQL Injection:** When dealing with dynamic queries or Content-Providers ensure you are using parameterized queries.
  * **JavaScript Injection (XSS):** Verify that JavaScript and Plugin support is disabled for any WebViews (usually the default).
  * **Local File Inclusion:** Verify that File System Access is disabled for any WebViews (webview.getSettings().setAllowFileAccess(false);).
  * **Intent Injection/Fuzzing:** Verify actions and data are validated via an Intent Filter for all Activities.

#### Reference

[OWASP Top 10 2014 - M7](https://www.owasp.org/index.php/Mobile_Top_10_2014-M7)