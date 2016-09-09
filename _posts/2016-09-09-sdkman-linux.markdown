---
layout: post
title:  "Ubuntu. Share SDKMAN/Grails/Groovy between Linux users."
date:   2016-09-09 12:00:01 +0100
categories: programming sdkman ubuntu linux grails groovy
---
Hi there! I hope you’re doing well :) Summer is gone but it’s nice autumn and
time for new fights with wins and loses :)

Some time ago I faced the problem: I needed Grails to be shared between 
different users on our server. Surprisingly I found that 
[SDKMAN](http://sdkman.io/install.html) installation doesn’t allow it out of the
box. The problem is that everything is installed in home directory of current
user. For example, I install SDKMAN as root user on my server. SDK is installed
to ```/root/.sdkman/```. After installation is finished you will see the text like: 
{% highlight console %}
Please open a new terminal, or run the following in the existing one:

source "/root/.sdkman/bin/sdkman-init.sh"
{% endhighlight %}

in the end of ```~/.bashrc``` and ```~/.profile``` you will also see something like:
{% highlight console %}
#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
export SDKMAN_DIR="/root/.sdkman"
[[ -s "/root/.sdkman/bin/sdkman-init.sh" ]] && source "/root/.sdkman/bin/sdkman-init.sh"
{% endhighlight %}

But how it’s going to work for other users? Let’s say I have ```another_user```
on the same server who is non-priviledged user. I want him to be able to use 
Grails which was installed by SDKMAN. I tried  ```source "/root/.sdkman/bin/sdkman-init.sh"```, 
but got error:
{% highlight console %}
-su: /root/.sdkman/bin/sdkman-init.sh: Permission denied
{% endhighlight %}

Frankly speaking I was disappointed :) 

After some time I found the solution:

1. [Uninstall SDKMAN](http://therealdanvega.com/blog/2015/10/14/uninstalling-gvm-or-sdk-man-on-mac-osx) 
    and all the shit that came with him.
    
2. Use shared folder which all the users can access for SDKMAN installation. In my case
 I installed to ```/usr/local/sdkman```. That’s pretty easy: ```export SDKMAN_DIR="/usr/local/sdkman" && curl -s "https://get.sdkman.io" | bash```. 
 [Installation instruction](http://sdkman.io/install.html) also tells about this option in the very bottom of
 the instruction, although I think it must be the default behaviour of their 
 installer.
 
3. Open ```~/.profile``` as ```another_user```(I think it must be something like ```/home/another_user/.profile``` on your computer) 
and copy here the lines from ```/root/.bashrc``` which come after ```#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!```

4. Login as ```another_user``` and try to enter ```sdk help``` in console. Now it should work.
 As well as all the Grails, Groovy, Gradle etc. which installed using this SDKMAN installation.
 For every user which you want to be able to use SDKMAN you have to add those lines to
 ```~/.profile``` as described above.

I hope this article helped you to save a little bit of your time :) Maybe some
of you know how to do it easier. Share your ideas about it in comments! 

Have a nice time and happy coding everybody!