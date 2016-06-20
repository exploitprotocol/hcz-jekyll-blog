title: Android Application Security Part 19 - Improper Session Handling
link: http://localhost/android-application-security-part-19/
author: exploitprotocol
description: 
post_id: 16023
created: 2015/10/13 21:54:48
created_gmt: 2015/10/13 21:54:48
comment_status: open
post_name: android-application-security-part-19
status: publish
post_type: post

# Android Application Security Part 19 - Improper Session Handling

Improper Session Handling holds **9th** position in [OWASP Mobile Top 10](https://www.owasp.org/index.php/Mobile_Top_10_2014-M8).

Session handling is very important part after authentication has been done. Session Management should also be done in secure way to prevent some vulnerable sceanarios. Most of the application have secure mechanism for authentication but very insecure mechanisms for session handling, below i will be describing some of the common scenarios.

### No session destruction at server side

I have seen this one most of the times, most of the applications just send a null cookie when user opt for logout but still that session cookie is valid on server side and is not destroyed after user opted for logout feature.

### Cookie not set as Secure

The secure flag is an option that can be set by the application server when sending a new cookie to the user within an HTTP Response. The purpose of the secure flag is to prevent cookies from being observed by unauthorized parties due to the transmission of a the cookie in clear text.

To accomplish this goal, browsers which support the secure flag will only send cookies with the secure flag when the request is going to a HTTPS page. Said in another way, the browser will not send a cookie with the secure flag set over an unencrypted HTTP request.