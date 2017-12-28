---
layout: post
title:  "Android. Delete System App using Droid Optimizer."
date:   2017-12-28 00:00:00 +0100
---
In this article I'm going to demonstrate my method of deleting Android system
applications using [Droid Optimizer](https://play.google.com/store/apps/details?id=com.ashampoo.droid.optimizer)
software. The UI of this software looks a little bit counter-intuitive to me and
a colleague of mine, so, I decided to write this post. Who knows, maybe it'll 
help somebody to save some time and nerves :)

Before I start describing the procedure, I want to warn you: _think twice, are
you sure you want to delete some system app(s)?_ My strong recommendation here
would be: *DO NOT DELETE ANY SYSTEM APP, TRY TO FIND ANOTHER WAY TO SOLVE YOUR
PROBLEM.* Deletion of system application(s) can ruin your system completely.

If you're reading this line you either know what you're doing or you're 
totally desperate to solve the problem in any other way without deleting 
the shit(that was my case, BTW). 

Ok, let's start. Here is the scenario which works for me: 

1. Run ```Droid Optimizer``` application.
2. If your device is rooted go to the settings page and click "gears" button in the
right bottom of the page: 
![Screenshot 1]({{ "/assets/2017_12_28/do_home_settings.png" | absolute_url }}) 
Select the check box "Device is rooted": 
![Screenshot 2]({{ "/assets/2017_12_28/do_settings.png" | absolute_url }})
3. Return back to the main screen and click "App Manager" button:
![Screenshot 3]({{ "/assets/2017_12_28/do_home.png" | absolute_url }})
4. Now you see the list of the applications. These are the current user's applications.
But that's not what you need, you're going to delete _system_ app, right? :) 
So, click on the column "User" and select "System":
![Screenshot 4]({{ "/assets/2017_12_28/do_app_manager.png" | absolute_url }}) 
![Screenshot 5]({{ "/assets/2017_12_28/do_app_manager_menu.png" | absolute_url }}) 
5. Now you see the long list of system applications where you can find the one
you want to delete:
![Screenshot 6]({{ "/assets/2017_12_28/do_app_manager_system.png" | absolute_url }})
6. If you found the desired app, click on it and press "Delete" button:
![Screenshot 7]({{ "/assets/2017_12_28/do_app_manager_delete.png" | absolute_url }})

In some cases your system will not allow you to delete the app - it will suggest you to
disable(freeze) the app instead.   

I hope this post helped you. If you have any questions/suggestions - don't
hesitate to write them in the comments below. 

I wish you a good day(or night???)! Happy coding! Bye-bye!
