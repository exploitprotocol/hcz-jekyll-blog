title: Android Application Security Part 12 - Poor Authentication And Authorization
link: http://localhost/android-application-security-part-12/
author: exploitprotocol
description: 
post_id: 16001
created: 2015/10/13 21:44:30
created_gmt: 2015/10/13 21:44:30
comment_status: open
post_name: android-application-security-part-12
status: publish
post_type: post

# Android Application Security Part 12 - Poor Authentication And Authorization

**Poor Authorization and Authentication** hold 5th position in OWASP Mobile Security Top 10. In this post i will be demonstrating some of the scenarios which falls under **Poor Authorization and Authentication** category.So here we Begin :)

### Activities Vulnerabilties

Most of the time after authentication on an Android Application , it shift to a new activity which basically users are aware off. But developers keep those activities exported and even without custom permissions.

  * If you would see in the HerdFinancial Application then you will find that **org.owasp.goatdroid.herdfinancial.activities.Main** is exported and also it doesn't even have any custom permissions.

  * You can simply pass an intent through Drozer to start that particular activity. ![](https://i.imgur.com/CqQbeyn.png)

  * After that you will see that Herfinancial Application has been started with default account i.e with the account number **1234567890** and now you can do sort of stuff like transfer the money to someone else account. How scary it would be if something like this exist for our Banking apps. ![](https://i.imgur.com/SQ0Z4LX.png)

### Username Enumeration Issue

Username Enumeration is a kind of flaw in which using some feature of an application we can figure out whether a particular username exists or not. I have tried to register with the username **aditya** but i already had an account with that username in that particular application. So application an message that "Username already registered". But this kind of behaviour inform about which users are existing on that particular application, now these usernames can be used to perform other attacks like bruteforce attacks for those particular username/password combination.

![](https://i.imgur.com/UKnSIsN.png)

### Brute Force Attacks

Most of the time developers place different implementation at backend. Like for the web application there is always an Brute-Force protection mechanism but in the case of mobile application rarely any application have such implementation at their server side.

### Insecure Authorization

Most of the application implement such authorization techiques which sometimes create very serious vulnerability. Below i will be describing such an example in which response from the server contains account number of that authenticated user. So we can change that account number to someone else account number and then we will completely own that account.

  * First open up your Burp Suite and turn Intercept On.

  * Then open up that HerdFinancial Application and type your credentials. ![](https://i.imgur.com/oQsuoTH.png)

  * Now the request will show up in Burp Suite ,forward it. ![](https://i.imgur.com/NCAv647.png)
  * Now response from server will contain accountnumber , as in my case it was **7894561230**. ![](https://i.imgur.com/qLlXW71.png)
  * You can change that accountnumber to someone else account number, like i changed from **7894561230** to **1234567890**. ![](https://i.imgur.com/9m3KxKw.png)

Now if you will use HerdFinancial Application then you will see that it has actually all the details of account **1234567890** and you can also make an transfer on behalf of **1234567890** . So that basically mean that you now own an Bank account of someone else just by knowing his/her account number.

### Authorize Hardware ID

If you would closely operate Herd Financial Application then you will find that there is an Authorize Device option there. HerdFinancial Application can also authorize on basis on Device Id but this is a flawed method as Device Id can be forged.

![](https://i.imgur.com/i8xJ2uc.png) ![](https://i.imgur.com/7sZB8NN.png) ![](https://i.imgur.com/TOygdbd.png)

  * After clicking yes in the above screen you will find a similar request in your BurpSuite panel. ![](https://i.imgur.com/lLqa4l9.png)