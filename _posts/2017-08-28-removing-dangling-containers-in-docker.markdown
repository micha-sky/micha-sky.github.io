---
layout: post
title:  "removing dangling containers in docker"
date:   2017-08-25 17:08:58 +0200
categories: development
---

when building a lot of containers docker can use up a lot of memory with
intermediate and dangling containers

{% highlight console %}
docker images -f dangling=true
{% endhighlight %}

{% highlight console %}
docker rmi $(docker images -f dangling=true -q)
{% endhighlight %}

to stop running containers
{% highlight console %}
docker stop `docker ps -qa`
{% endhighlight %}

to remove running containers
{% highlight console %}
docker rm `docker ps -qa`
{% endhighlight %}
