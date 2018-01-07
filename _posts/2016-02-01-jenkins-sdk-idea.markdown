---
layout: post
title:  "Java SDK for Jenkins API. The idea."
date:   2016-02-01 04:09:01 +0100
categories: programming opensource jenkins
tags: [java, jenkins, sdk, client, jenkinssdk, jenkinsclient, jenkinsjavaclient]
---
I work in a company that uses [Jenkins](https://jenkins-ci.org/) as a CI server. 
Our infrastructure was growing and we 
were automating it using some Groovy scripts. Sometimes we have situations where
we need to read some build information from Jenkins or download artifacts or 
trigger some builds. I want to put all those pieces of code into something re-usable.

During the time of creating automation scripts I got some experience with 
[Jenkins Remote Access API](https://wiki.jenkins-ci.org/display/JENKINS/Remote+access+API).
I believe, I'm able to summarise my knowledge and create a small library which
will probably save some time for someone who will face the same issues that I
did.

Another thing is that I almost have no experience with open source projects. 
It's a shame, I know that :) Sometimes I ask myself: do you know how to put
a library to any public Maven repository? Don't you want your creature to be
available at [http://mvnrepository.com/](http://mvnrepository.com/)? The answer was always: "Yes, but..."

I spent New Year in my bed because I was ill. During this illness time I was 
thinking a lot(normally it doesn't happen to me :)). I was thinking about 
future, plans and meaning of life. Finally, I saw this brilliant 
[article](http://www.yegor256.com/2015/12/22/why-dont-you-contribute-to-open-source.html) by 
Yegor Bugayenko. Then I decided to act: stop thinking, start doing! :)

I created [Github project](https://github.com/aistomin/jenkins-sdk) for my 
Jenkins SDK idea. Now it's in progress. Daily I'm trying to spend some minutes
to make at least small contribution. I hope to finish the basic version in the 
first days of March.

That's what I wanted to share with you in this post. Maybe you have some 
thoughts about it? Don't hesitate to share your point of view in comments:

- Do you think somebody needs such a library?
- Would you like to help me with implementation?
- Don't you think that it's just a wasting of time?

Have a good time and happy coding everybody!