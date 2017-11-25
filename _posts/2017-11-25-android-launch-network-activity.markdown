---
layout: post
title:  "Android. How to launch System NetworkActivity programmatically."
date:   2017-11-25 00:00:00 +0100
---
Recently I faced the problem when I needed to have a full network management functionality
in my Android TV application. Everything I found with quick google search is how to run
system WIFI management activity using ```Settings.ACTION_WIFI_SETTINGS``` or
```Settings.ACTION_WIRELESS_SETTINGS```. But this solution didn't fully cover my requirements
 because it didn't allow to manage Ethernet connections, for example. After spending quite
 some time I found the way to launch the activity which allows to manage all possible network
 sources.


As I said, I spent quite some time googling and trying to find the solution. Maybe my googling
 skills are not that strong, maybe my understanding of Android world is not that deep and I
 used wrong terms in my queries, whatever, I almost gave up the idea of using standard tools for
 network management and was about to start implementing my own monster.

 Suddenly, playing around with Android emulator, I noticed the following line in logcat:

 ```
 11-25 09:04:16.208 1605-1763/system_process I/ActivityManager: START u0 {cmp=com.android.tv.settings/.connectivity.NetworkActivity} from uid 1000 on display 0
 ```

 This line appeared in exact the moment when I was clicking standard Android settings. This piece of
 information gave me an idea of which component should I use. Soon the solution for my problem was found:

 ```
 public void openNetworkActivity() {
    final Intent intent = new Intent("com.intent.MAIN");
    intent.setComponent(
        ComponentName.unflattenFromString(
            "com.android.tv.settings/.connectivity.NetworkActivity"
        )
    );
    startActivity(intent);
 }
 ```

 The code above is the method of activity from where you plan to launch network settings.

 Note: This solution works perfect for me because I have fixed type of device and Android
 version. If you plan to use it in your application you need first to research if such a
 component available at any device where you plan to run your application.

 I hope this post will help somebody to save some time and effort.

 Have a good time! Bye!

