---
layout: post
title:  "A Few Practical Tips for Junior Developers."
date:   2017-02-01 00:00:00 +0100
---
Many of us are used to be annoyed by colleagues. That's just the thing nobody can
avoid working in a team: people have different points of view, different habits,
different capabilities etc. But how often do we think about ourselves being an asshole
who annoys the others? That's I believe the thing we should always care about. It's not
easy at all, but I have a few thoughts which I would like to share with
you. Maybe it will help you to be more effective and less annoying :) The post was
planned as a post for junior developers. Though, I know for sure that many "Senior"
developers have no idea about those basic things which I'm going to say now.
They just don't care. Actually, everything I'm going to say in this post is as simple
as washing your hands before lunch. Let's go:

Ok, first let's remember the problems we all know:

* "This idiot said the problem is solved but it's still there! Is it so difficult
 just to fix this typo in label's text?"
* "This asshole pushed some crap and the red build is blocking my work now."
* "This imbecile is not able even to use IDE for code formatting." another
    variant: "This dumbass reformatted all the code in the whole project using his f*cking IDE"
* "Console outputs in production code? Seriously?"
* "The code can not even be compiled after this changes(facepalm)".
* And, my favourite, the situation of "Some fixes" commit message in VCS history.

Of course, this list of small annoying problems can be endless, but I hope you got the
idea what really enrages me :)

So, I suggest a few really easy steps, which help to avoid many of those problems:

1. **Read the task description carefully**. Don't start working until you understand the task 100%.
2. If it's a bug, **reproduce it** first. If you can not reproduce it don't even try
to solve it. If you're lucky to reproduce it - remember the scenario, you will need
it later to verify your results.
3. Thinking, debugging, coding etc. Let's assume you know what you're doing there
and let's move on to the point where you think you're ready to finish with the task :)
4. **Check your results locally**. Do not assume that it's working. Run the system, click
around. If it's a bug, follow the scenario from (2) and make sure the problem is solved.
5. **Run all the tests**(if you have them).
6. **Review your code before commit**. Yes, even if you changed 100 files and 10000 lines
of code. Just f*cking do it!!! Please. Do it even more carefully if you're committing
1 line of changes which "will obviously work". Enjoy every time when you find nothing
during review. I never thought about it deeply, but I have a feeling that in 90% of
cases I find something during such a review.
7. Commit your changes. **Write the informative commit message**. "bugfix" or
"some improvements" are not an informative messages to me. Ticket number from your
issue-tracking system + clear explanation of what was changed and why. That's what I would
appreciate.
8. If you have a CI, please, **wait for green build**. I know, it's already 17:57 and you have
to go, but, please, wait... I would even recommend not to share your changes with a team if you
do not plan to stay for a next couple of hours.
9. Build is green. Go and take some sweeties! :) Well done!

I'm not naive and I do not believe those small tips will save the world. But they will
minimise your risk of being asked "WTF is this?". Of course, we're all humans and we're
making mistakes. Following my tips, you will not stop making mistakes. But I really do
believe that it will help you to become more reliable for your colleagues. Just follow
those steps and you will be better than many of those developers which I met in my life.


Share your ideas and your tips in comments! :)

See you soon, happy coding! Bye, bye!

P.S. Tip #0. Choose a <s>convenient</s> <s>commercial</s> JetBrains IDE for creating your code and pay attention to the
warnings and hints that it offers you. IDE is your friend and helper. Unless you use Eclipse, of course.