---
layout: post
title:  "Android TV Box. Autolauncher problems with Android 7(Nougat). My solution."
date:   2018-01-06 00:00:00 +0100
tags: [android, nougat, androidtv, webchip, autolauncher, bug, kioskmode, homeapp, reboot]
---
I found out that auto-launching feature doesn't work properly on my 
[WeChip](http://www.wechipbox.com/) device with Android 7 installed on it. It
worked perfectly with Android 6, but with Android 7 after device reboot
I still get default screen instead of my own application which is configured
as "Home application". In this post I'm going to share the solution which
I consider as acceptable for my case. This solution is applicable 
_only for rooted devices_.

My goal was to have a "kiosk" mode on the Android TV device. Which means that
end user must see only my application on this device and nothing else. For the
previous version of Android this task was easy to solve: I just needed to 
configure my application as "Home application" and every time I switched the 
device on, my application was launched automatically. Also, if I pressed "Home"
button on the remote control -> my application was launched.

Then I received the device with Android 7.1.2 on it. "Home" button still works
perfect, but when I reboot the device I see the default device's home 
screen and I always need to launch my application manually. I saw some people had 
already faced [the same problem](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s912/vontar/firmware-roms-aa/672655-%7Brom%7D-new-firmware-sunvell-t95z-plus-tv-box-android-7-1-1-with-root?p=673951#post673951)
when they were trying to setup some custom launcher instead of the default one,
which comes with the device.

I spent quite some time trying to solve the problem. I didn't find any nice
and perfect solution. Finally, I ended up with a kind of "acceptable" solution.
This solution may look odd and I would really appreciate if somebody could 
suggest the proper(or better) solution in the comments below. 

Anyways, let me try to describe what I've found and what helped me :) Important
remark: _provided, that device is rooted_. I'm still not sure who is responsible
for this problem: is it a default launcher bug or firmware POM defect or anything else.
In a short words, I had just disabled the default launcher(in my case it was
SWin8Launcher) and got the desired behaviour of the device: end user can use
only my application, everything else is just not available for him/her. For the
future simplicity I will refer the target application (which you want to be
launched at startup and to be your default home application) as 
_Custom Launcher_.

Here are the steps:
1. Install Custom Launcher application and configure it as "Home application"
of the device. 
2. Using [Droid Optimizer]({% post_url 2017-12-28-how-to-delete-android-system-app-using-droid-optimizer %}) 
find and disable SWin8Launcher application.
3. Reboot the device.
4. Now your Custom Launcher is a default launcher of the device :) 
 
Let me know guys what do you think about the issue and my solution to it in the
comments below.

I wish you a good luck! See you soon! Bye!
