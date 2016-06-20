title: Appie New Release - Update Instructions Included
link: http://localhost/appie-release/
author: exploitprotocol
description: 
post_id: 9648
created: 2015/02/28 18:53:01
created_gmt: 2015/02/28 18:53:01
comment_status: open
post_name: appie-release
status: publish
post_type: post

# Appie New Release - Update Instructions Included

First of all i would like to thank everyone for their support in making Appie a Huge Success. It is only one month after releasing Appie and i have received awesome response from the users. Within one month there are about [2250 downloads](https://sourceforge.net/projects/appiefiles/files/Appie.zip/stats/timeline?dates=2015-01-16+to+2015-03-1) of Appie which is highest for any existing alternative to Appie. See [here](https://manifestsecurity.com/appie/#WhatTheyAreSaying) about Appie journey till now.

There were so many suggestion about tools which users wanted to see in Appie. So this release contains majorly some tools which people suggested which will be helpful to the community and there are some configuration changes as well which makes Appie more fast and efficient. With the addition of tools given below, Appie is now capable for **Android Application Security Assessment, Android Forensics, Android Malware Analysis.**

Below are the tools which are included in Appie in this release.

  * This is one of my favourite tools. As most of Android Security Professionals need to use logcat but there is no option to view logcat for a specific application. So i have included [Pidcat](https://github.com/JakeWharton/pidcat) in this release. Also pidcat show log entries in a coloured manner, which makes pentesting much more awesome.

In order view logcat entries for **org.owasp.goatdroid.fourgoats**, type **pidcat org.owasp.goatdroid.fourgoats** in Appie and you would see something similar. ![](https://i.imgur.com/BJWGslG.png)

  * [Burp Suite](http://portswigger.net/burp/download.html) \- This was suggested by so many people and it was great idea to embed BurpSuite in Appie so that we have everything inside Appie.

Type **burp** in the Appie console to open up BurpSuite. ![](https://i.imgur.com/u9uAFzV.png)

  * [AndroGuard](https://github.com/androguard/androguard) \- This was something which was mostly suggested because most of the Android Pentesting Platforms do not have proper installation of Androguard and in some of those it doesn't even work but in Appie i have configured in a way to run properly.

  * [Androwarn](https://github.com/maaaaz/androwarn) \- This is an awesome static code analyzer for malicious android application.

Type **androwarn** in the console to open androwarn directory and then see [usage](https://github.com/maaaaz/androwarn#usage) for it's usage.

  * [Java Debugger](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/jdb.html)

  * [Volatility Framework](https://github.com/volatilityfoundation)\- volatility which an advanced memory forensics framework is include in this release.

Type **volatility** in the console to use this. ![](https://i.imgur.com/c4CJOsr.png)

  * [Wireshark](https://www.wireshark.org/) \- Wireshark is include in this release and it also opens within Appie.

Type **wireshark** in Appie console to open wireshark within Appie. ![](https://i.imgur.com/aOsTSiI.png)

## How to Update

First release of Appie was of nearly **600MB** but this release it of nearly **800MB** as it contains some new tools . So size is something which is not in my control but it is still very less compared to other alternatives which are atleast of **8GB**.

But i am aware how painful it is to download such large when there is an update,so for our existing users i have made an update which is only **180 MB**, so it create a less burden on your internet usage and also less time to update Appie. You have only to copy folders from update.zip file to Appie directory and Appie will work with new tools.

  * Extract Update_V1.zip file and then you will see folders like given below. ![](https://i.imgur.com/D9KwJnG.png)

  * Copy those folder and paste them in to Old Appie Folder and Click on **Replace All Files** option when asked and you are done. ![](https://i.imgur.com/glyH4Ep.png)

New Release Download Link ![Download Appie](https://a.fsdn.com/con/app/sf-download-button)

Update Link ![Update](https://a.fsdn.com/con/app/sf-download-button)

If you have something in mind which can make Appie more better then please let me know through [Twitter](https://twitter.com/exploitprotocol) or by shooting an email to **aditya@manifestsecurity.com** .If you want to suggest but in Anonymous way then please use the form below.

Loading...