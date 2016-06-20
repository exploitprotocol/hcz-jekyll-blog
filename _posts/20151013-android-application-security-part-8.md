title: Android Application Security Part 8 - Insecure Data Storage
link: http://localhost/android-application-security-part-8/
author: exploitprotocol
description: 
post_id: 15953
created: 2015/10/13 03:02:00
created_gmt: 2015/10/13 03:02:00
comment_status: open
post_name: android-application-security-part-8
status: publish
post_type: post

# Android Application Security Part 8 - Insecure Data Storage

Insecure Data Storage hold **2nd** position at [OWASP Mobile Top 10](https://www.owasp.org/index.php/Mobile_Top_10_2014-M2).

Our common concern remain that our application data is securely stored on our android devices so that no one can extract data from it in the case of theft or loss. Also one application(malicious) cannot access data of another application (Banking).

### Threat Agents

  * Mobile Malwares

  * Physical Access to device

### Internal Storage

As i have mentioned in one of my previous blog post that by default, files that you create on internal storage are accessible only to your app. This protection is implemented by Android and is sufficient for most applications.

But developers often use `MODE_WORLD_READBALE` & `MODE_WORLD_WRITABLE` to provide those files to some application but this doesn't limit other apps(malicious) from accessing them. 

For Demonstration i have used FourGoats App.Every App data resides in /data/data/ in an Android Device. In each application folders there is a `shared_prefs` and database folder and several other folders as implemented by application. Files under these folders come under Internal Storage Category. In most of the apps you will find that files in the shared_prefs folder are world readble and even files with sensitive data are Public.

![](https://i.imgur.com/jecmrV5.png)

In the above picture you can see that all the files in the shared_prefs folder of FourGoats App is world readable. So any malicious app can access the content of those files on a non-rooted device also. The prime concern over here is that sometimes developers also store username-password pairs in the following files which can lead to compromise of user account. 

**How to Fix**

  * Do not use `MODE_WORLD_WRITEABLE` or `MODE_WORLD_READABLE` modes for IPC files because they do not provide the ability to limit data access to particular applications, nor do they provide any control on data format.If you want to share data with other apps then use content provider instead which offers read and write permissions to other apps and can make dynamic permission grants on a case-by-case basis.

  * Avoid exclusively relying upon hardcoded encryption or decryption keys when storing sensitive information assets because those keys can be retrived after decompiling the app.

  * Consider providing an additional layer of encryption beyond any default encryption mechanisms provided by the operating system.

### External Storage

Files created on external storage, such as SD Cards, are globally readable and writable. Because external storage can be removed by the user and also modified by any application, you should not store sensitive information using external storage.

As with data from any untrusted source, you should perform input validation when handling data from external storage. We strongly recommend that you not store executables or class files on external storage prior to dynamic loading. If your app does retrieve executable files from external storage, the files should be signed and cryptographically verified prior to dynamic loading.

### Content Providers

Note: There is a seperate post on [Attacking Content Providers](https://manifestsecurity.com/android-application-security-part-15), you can skip this for now .

I have already discussed about content providers and ways in which apps can store and share data throught it. Please revisit [here](https://manifestsecurity.com/android-application-security-part-3/#ContentProvider) to know more about it.

Below i am using Sieve app to demonstrate vulnerability .Sieve is made by the company who made the awesome tool **Drozer** which we have been using in the past and will continue to use that in the upcoming post.

Lets get started. ![](https://i.imgur.com/cnbHEO0.png) we can see there are two exported Content Providers. ![](https://i.imgur.com/1ON88Jy.png) So by using **app.provider.finduri** module we have found some of the exported content provider URIs which can be accessed by other apps installed on the same device.

We can see that there are two similar URIS **content://com.mwr.example.sieve.DBContentProvider/keys** & **content://com.mwr.example.sieve.DBContentProvider/keys/** Let's try to query each of them. ![](https://i.imgur.com/T6P7VM4.png) ![](https://i.imgur.com/1pGXATa.png) Upon accessing the first one need **com.mwr.example.sieve.READ_KEYS** permission but second one doesn't need any permission.So now we have the master password and pin of the App which manages other Apps password.**Isn't that Dangerous**.

Let's try to change the value of **Password** from **iampassword1234** to **iampassword5555** ![](https://i.imgur.com/c3P6DpQ.png) We can also access the password's saved in this Password Manager App by query another exported URI. ![](https://i.imgur.com/018cbFR.png) I would advise you to try above drozer module for this vulnerable application and if you stuck with any module then just run that command with --help switch.

**How TO Fix**

  * If your content provider is just for your app’s use then set it to be android:exported=false in the manifest. If you are intentionally exporting the content provider then you should also specify one or more permissions for reading and writing.

  * If you are using a content provider for sharing data between only your own apps, it is preferable to use the android:protectionLevel attribute set to "signature" protection.

  * When accessing a content provider, use parameterized query methods such as query(), update(), and delete() to avoid potential SQL injection from untrusted sources. 

#### Reference

[OWASP Top 10 2014 - M2](https://www.owasp.org/index.php/Mobile_Top_10_2014-M2)

[Security Tips | Android Developers](http://developer.android.com/training/articles/security-tips.html)