---
layout: post
title:  "Groovy's .equals() method uses .compareTo() under the hood."
date:   2017-03-17 00:00:00 +0100
tags: [groovy, equals, compareto, bug]
---
Today a colleague of mine shared a curious observation. He found out
that ```.equals()```(or ```==```) in Groovy does something different from
what we would expect in Java. Oddly enough, it uses ```compareTo()``` method
under the hood. I've made some code samples. Let's look at them.

**Test case:**

1. We have a class with some ```Long``` identifier field called ```id```.
2. The class implements ```Comparable``` interface and ```compareTo()``` compares the ```id``` values.
3. We have two instances of this class with ```id = 1```.
4. The expected behaviour is that first instance is not equal to the second one.

**Java example:**

{% highlight java %}
@Test
public void testEquals() {
    System.out.println("Test is started.");
    final MyClass first = new MyClass(1L);
    final MyClass second = new MyClass(1L);
    Assert.assertTrue(!first.equals(second));
    Assert.assertTrue(first != second);
    System.out.println("Test is finished.");
}

final class MyClass implements Comparable<MyClass> {

    private final Long id;

    MyClass(final Long id) {
        this.id = id;
    }

    public int compareTo(MyClass o) {
        System.out.println("MyClass.compareTo");
        return this.id.compareTo(o.id);
    }
}
{% endhighlight %}

The output is:
{% highlight console %}
Test is started.
Test is finished.
{% endhighlight %}

**The same example in Groovy(I'm using Grails 2.5.5 + JUnit 3 for testing):**

{% highlight groovy %}
void testEquals() {
    println "Test is started."
    final first = new MyClass(1)
    final second = new MyClass(1)
    assertTrue(!first.equals(second))
    assertTrue(first != second)
    println "Test is finished."
}

final class MyClass implements Comparable<MyClass> {

    private final Long id

    MyClass(final Long id) {
        this.id = id
    }

    int compareTo(MyClass o) {
        println "MyClass.compareTo"
        return this.id <=> o.id
    }
}
{% endhighlight %}

The output is:
{% highlight console %}
--Output from testEquals--
Test is started.
MyClass.compareTo
| Failure:  testEquals()
|  junit.framework.AssertionFailedError

{% endhighlight %}

**The odd things are:**

1. ```MyClass.compareTo()``` was called.
2. As a result, both expressions: ```assertTrue(!first.equals(second))``` and ```assertTrue(first != second)``` fail.

I do not want to write any conclusion there, because I didn't investigate the problem in details. It's just a curious fact
that I want to share with you. I'm not even sure is it a desired behaviour or just a bug. Share your thoughts in comments.

Keep on coding and be careful using Groovy! :)
