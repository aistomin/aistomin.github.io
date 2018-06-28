---
layout: post
title:  "Android TV. Use 'Droid TV Settings' inside your App."
date:   2018-06-28 00:00:00 +0100
tags: [android, droidsettings, droidtvsettings androidtv, kioskmode, khadas, androidtvapp, androidtvapplication]
---
Building your Android TV application you will probably need to give your users a possibility 
to configure or set up some system settings. There are a lot of standard settings which you 
won't like to implement yourself. The easiest solution I found is to use "Droid Settings" or 
"Droid TV Settings" application, which was already installed on my Android TV Box, by 
embedding it's UI inside my application. In this post I'm going to show you a working example
of how I did it.

First of all I want to make sure my reader understands which "Droid Settings" do I mean. 
I'm talking about [this](https://github.com/khadas/android_vendor_amlogic_apps_DroidTvSettings)
application. You may easily check if it's installed on your box or not by searching for
the following icon in the installed applications list:

![Screenshot 1]({{ "/assets/2018_06_28/droid_settings_icon.png" | absolute_url }})

If this application is not installed, then you probably need to install it or find 
another solution to your problem. 

If you have this application on your device, then we can use it. We're going to use
similar technique as I used to launch network settings in one of my 
[previous posts]({% post_url 2017-11-25-android-launch-network-activity %}). 
Using ```adb logcat``` we can find the "Droid Settings" component name and then just
launch it from our application. In the example below, I will show you how to call the whole
"Droid Settings" application and how to launch only specific part of it.

Let's start. 

Let's assume we have an Android application which has some activity with 2 buttons:
first one is for calling the whole "Droid Settings" app, the second is for calling
only, let's say, "Display" settings part. The UI of such an application would look
something like that:

![Screenshot 2]({{ "/assets/2018_06_28/main.png" | absolute_url }})

First of all, let's create a method which can launch any system component installed on
the device:
{% highlight java %}
void launchComponent(
    final Context context, final String comp
) {
    try {
        final Intent intent = new Intent("com.intent.MAIN");
        intent.setComponent(ComponentName.unflattenFromString(comp));
        context.startActivity(intent);
    } catch (final ActivityNotFoundException exception) {
        Toast.makeText(
            context, String.format("Component %s not found.", comp),
            Toast.LENGTH_LONG
        ).show();
    }
}
{% endhighlight %} 

Let's implement the logic of the button which calls the whole "Droid Settings" app. 
The component name, as I mentioned before, I found in ```adb logcat``` logs
just by launching "Droid Settings" from the "Apps" menu and "grep"-ing the result.
The code would look like:
{% highlight java %}
findViewById(R.id.btnMain).setOnClickListener(
    new View.OnClickListener() {
        @Override
        public void onClick(final View view) {
            launchComponent(
                MainActivity.this,
                "com.droidlogic.tv.settings/.MainSettings"
            );
        }
    }
);
{% endhighlight %} 

If we run our application and click on the button we will see the following:

![Screenshot 3]({{ "/assets/2018_06_28/all.png" | absolute_url }})

I think, you already got the idea. The ```MainSettings``` activity and 
the ```com.droidlogic.tv.settings``` package are clearly visible in the 
"Droid Setting" [source code](https://github.com/khadas/android_vendor_amlogic_apps_DroidTvSettings).
Thus, if we want to call only some particular part of it(the sub-settings of this application are
very well structured in separated activities), we just need to find this activity inside the code and
use the default application package. Just like that:
{% highlight java %}
findViewById(R.id.btnDisplay).setOnClickListener(
    new View.OnClickListener() {
        @Override
        public void onClick(final View view) {
            launchComponent(
                MainActivity.this,
                "com.droidlogic.tv.settings/.display.DisplayActivity"
            );
        }
    }
);
{% endhighlight %} 

Let's run the app and click on the button:

![Screenshot 4]({{ "/assets/2018_06_28/display.png" | absolute_url }})

I hope this article will help you. The working code of the given examples you may find [here](https://github.com/aistomin/droid-settings-launcher).

Let me know what do you think about my solution in the comments below. Don't hesitate 
to share your opinion or ask any questions.

Have a good time! Happy coding! See you soon! Bye-bye!
