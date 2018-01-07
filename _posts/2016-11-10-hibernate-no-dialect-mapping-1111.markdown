---
layout: post
title:  "Hibernate. No Dialect mapping for JDBC type: 1111."
date:   2016-11-10 20:00:01 +0100
categories: hibernate grails gorm postgres
tags: [hibernate, jdbc, error, 1111]
---
Hello coders!
I'll try to explain the problem and show my solution to it using Grails code 
examples and PostgreSQL. I believe the problem is general for Hibernate and
similar exception can happen with other dialects as well. I'll try to 
demonstrate my solution for PostgreSQL. Maybe it'll help you.

So, let's imagine we have code like that:
{% highlight groovy %}
SomeGORMEntity.withSession { final org.hibernate.Session session ->
    session.createSQLQuery('SELECT pg_sleep(1)').list()
}
{% endhighlight %}

we will get an exception like this:

{% highlight console %}
No Dialect mapping for JDBC type: 1111; nested exception is org.hibernate.MappingException: No Dialect mapping for JDBC type: 1111
org.springframework.orm.hibernate4.HibernateSystemException: No Dialect mapping for JDBC type: 1111; nested exception is org.hibernate.MappingException: No Dialect mapping for JDBC type: 1111
	at org.springframework.orm.hibernate4.SessionFactoryUtils.convertHibernateAccessException(SessionFactoryUtils.java:218)
	at org.codehaus.groovy.grails.orm.hibernate.GrailsHibernateTemplate.convertHibernateAccessException(GrailsHibernateTemplate.java:606)
	at org.codehaus.groovy.grails.orm.hibernate.GrailsHibernateTemplate.doExecute(GrailsHibernateTemplate.java:192)
	at org.codehaus.groovy.grails.orm.hibernate.GrailsHibernateTemplate.execute(GrailsHibernateTemplate.java:132)
	at org.codehaus.groovy.grails.orm.hibernate.HibernateGormStaticApi.withSession(HibernateGormStaticApi.groovy:487)
{% endhighlight %}

If I understand correctly, Hibernate has a problem with recognising the type of
the the value that is returned by such a query.

The workaround I found is this:

{% highlight groovy %}
SomeGORMEntity.withSession { final org.hibernate.Session session ->
    session.createSQLQuery('SELECT CAST(pg_sleep(1) AS VARCHAR)').list()
}
{% endhighlight %}

I simply cast the type which Hibernate can not recognise(I believe this type is
```VOID```) to ```VARCHAR``` which Hibernate understands perfectly.

I hope this article helped you. Share your ideas in comments :) 

Happy coding. CU :)