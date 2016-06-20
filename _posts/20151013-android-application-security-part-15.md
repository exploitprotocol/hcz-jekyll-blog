title: Android Application Security Part 15 - Attacking Content Providers
link: http://localhost/android-application-security-part-15/
author: exploitprotocol
description: 
post_id: 16013
created: 2015/10/13 21:49:34
created_gmt: 2015/10/13 21:49:34
comment_status: open
post_name: android-application-security-part-15
status: publish
post_type: post

# Android Application Security Part 15 - Attacking Content Providers

I have already described about Content Providers in [Android Application Security Part 3- Android Application Fundamentals](http://manifestsecurity.com/android-application-security-part-3/), please go through it if you haven't yet.

In this post i will be showing to exploit another vulnerable app [Sieve](https://www.mwrinfosecurity.com/products/drozer/community-edition/). Sieve is made by the company who made the awesome tool **Drozer** which we have been using in the past and will continue to use that in the upcoming post.

Lets get started. ![](https://i.imgur.com/cnbHEO0.png) we can see there are two exported Content Providers. ![](https://i.imgur.com/1ON88Jy.png) So by using **app.provider.finduri** module we have found some of the exported content provider URIs which can be accessed by other apps installed on the same device.

We can see that there are two similar URIS **content://com.mwr.example.sieve.DBContentProvider/keys** & **content://com.mwr.example.sieve.DBContentProvider/keys/** Let's try to query each of them. ![](https://i.imgur.com/T6P7VM4.png) ![](https://i.imgur.com/1pGXATa.png) Upon accessing the first one need **com.mwr.example.sieve.READ_KEYS** permission but second one doesn't need any permission.So now we have the master password and pin of the App which manages other Apps password.**Isn't that Dangerous**.

Let's try to change the value of **Password** from **iampassword1234** to **iampassword5555** ![](https://i.imgur.com/c3P6DpQ.png) We can also access the password's saved in this Password Manager App by query another exported URI. ![](https://i.imgur.com/018cbFR.png) I would advise you to try above drozer module for this vulnerable application and if you stuck with any module then just run that command with --help switch.

**How TO Fix**

  * If your content provider is just for your app’s use then set it to be android:exported=false in the manifest. If you are intentionally exporting the content provider then you should also specify one or more permissions for reading and writing.

  * If you are using a content provider for sharing data between only your own apps, it is preferable to use the android:protectionLevel attribute set to "signature" protection.

  * When accessing a content provider, use parameterized query methods such as query(), update(), and delete() to avoid potential SQL injection from untrusted sources.