---
layout: post
title: Where are my log files located?
date:   2014-10-29 12:38:28
position: 1
categories: faq
---

Each application and services which rapidcloud.io sets up has their own set of log files, which are generally configured to output into the /var/log directory. Below we enumerate some of our managed services and where you can expect to find the log output.

## Play

Your Play! application is installed in

<code>/opt/play</code>

It is organized into two folders which the deployer switches back and forth between during parallel deployments (if enabled).

1. /opt/play/9000
1. /opt/play/9001

Each instance has its own log directory

1. /opt/play/9000/logs
1. /opt/play/9001/logs

Standard error and standard out are written to 

1. /var/log/play/play_9000.err.log
1. /var/log/play/play_9000.out.log
1. /var/log/play/play_9001.err.log
1. /var/log/play/play_9001.out.log

## Tomcat

Tomcat is installed in

<code>/opt/tomcat/</code>

Tomcat is separated into a home and base for each instance.

{% highlight bash %}
CATALINA_HOME=/opt/tomcat
CATALINA_BASE=/opt/tomcat/instances/(8080|8081)
{% endhighlight %}


Each instance has its own log directory

1. /opt/tomcat/instances/8080/log/
1. /opt/tomcat/instances/8081/log/

Standard error and standard out are written to

1. /var/log/tomcat/tomcat_8080.err.log
1. /var/log/tomcat/tomcat_8080.out.log
1. /var/log/tomcat/tomcat_8081.err.log
1. /var/log/tomcat/tomcat_8081.out.log



## Nginx

Nginx is installed in

<code>/opt/nginx </code>

Nginx is configured to write errors out to standard error and the access log is disabled by default. 

You can change these settings by editing your nginx.conf file located at

<code>/etc/nginx/nginx.conf </code>

Standard error and standard out are written to

1. /var/log/nginx/nginx.err.log
1. /var/log/nginx/nginx.out.log

## Supervisord

Supervisord writes its logs to

1. /var/log/supervisor/supervisord.log