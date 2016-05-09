---
layout: post
title:  "redis shutdown issues"
date:   2016-05-09 10:17:58 +0200
categories: development
---
when using redis servers with password authentication you may experience problems with shutting down server.
it took sometimes up to 5 minutes to shut down server until i foudn out that redis was the problem.

the solution si simple: edit the /etc/init.d/redis_6379  file to "stop" section

add -a "yourredispassword"
{% highlight console %}
CLIEXEC -p $REDISPORT shutdown
{% endhighlight %}

then your redis service will shutdown quickly