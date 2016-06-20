title: Android Application Security Part 4-Understanding Android Manifest File
link: http://localhost/android-application-security-part-4-understanding-android-manifest-file/
author: exploitprotocol
description: 
post_id: 1535
created: 2015/01/03 13:33:24
created_gmt: 2015/01/03 13:33:24
comment_status: open
post_name: android-application-security-part-4-understanding-android-manifest-file
status: publish
post_type: post

# Android Application Security Part 4-Understanding Android Manifest File

Hello, In this post i will be discussing about the AndroidManifest.xml file which i have decribed in the last post. AndroidManifest.xml file is the essential part of the Android App and should be contained in the root Directory of the app. 

> 
>     <?xml version="1.0" encoding="utf-8"?>
>     <manifest>
>         <uses-permission />
>         <permission />
>         <permission-tree />
>         <permission-group />
>         <instrumentation />
>         <uses-sdk />
>         <uses-configuration />  
>         <uses-feature />  
>         <supports-screens />  
>         <compatible-screens />  
>         <supports-gl-texture />  
>         <application>
>             <activity>
>                 <intent-filter>
>                     <action />
>                     <category />
>                     <data />
>                 </intent-filter>
>                 <meta-data />
>             </activity>
>             <activity-alias>
>                 <intent-filter> . . . </intent-filter>
>                 <meta-data />
>             </activity-alias>
>             <service>
>                 <intent-filter> . . . </intent-filter>
>                 <meta-data/>
>             </service>
>             <receiver>
>                 <intent-filter> . . . </intent-filter>
>                 <meta-data />
>             </receiver>
>             <provider>
>                 <grant-uri-permission />
>                 <meta-data />
>                 <path-permission />
>             </provider>
>             <uses-library />
>         </application>
>     </manifest>

  * It declares the minimum level of the Android APi that the application requires.Syntax: 
    
        <uses-sdk android:minSdkVersion="integer"
      android:targetSdkVersion="integer"
      android:maxSdkVersion="integer" />
    

For example Android 4.4 has the API level 19 and if minSdkVersion is defined as 19 then that app can only run with Android 4.4 or above.