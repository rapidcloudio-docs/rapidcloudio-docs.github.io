---
layout: post
title: What types of applications are supported?
date:   2014-10-29 12:38:28
position: 1
categories: faq
---
Rapidcloud.io supports the management and deployment of Play 2 Web applications (built with sbt) or Java web applications packaged into a war file with Maven. 

Play applications are launched from the command line while Maven projects have their war file deployed to Tomcat.


## Play Framework 2

The default build command for Play applications

{% highlight bash %}
sbt clean compile stage -Dsbt.log.noformat=true
{% endhighlight %}

After compiling rapidcloud.io will copy your application files from

<code>target/universal/stage/</code> 

to 

<code>/opt/play/(9000|9001)/</code> 

then start your application by executing the command in 

<code>/opt/play/(9000|9001)/bin</code>

Note: Command line arguments can be provided on the server configuration page.


## Maven (Tomcat)

The default build for Maven applications
{% highlight bash %}
mvn clean package
{% endhighlight %}
The output from this command must produce a war file in the <code>target/</code> directory, otherwise rapidcloud.io will mark the deployment as failed.
