---
layout: post
title:  "set up java environment on ubuntu"
date:   2015-12-04 00:39:58 +0200
categories: deployment
---
this article is about setting up proper jre & jdk on ubuntu linux.

first, let's install default jre & jdk

{% highlight console %}
sudo apt-get install default-jre
sudo apt-get install default-jdk
{% endhighlight %}

then we add webupd8team repository
{% highlight console %}
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
{% endhighlight %}

let's install oracle's java 6,7,8
{% highlight console %}
sudo apt-get install oracle-java6-installer
sudo apt-get install oracle-java7-installer
sudo apt-get install oracle-java8-installer
{% endhighlight %}

setting up JAVA_HOME variable to java-8-oracle
{% highlight console %}
sudo update-alternatives --config java
export JAVA_HOME=/usr/lib/jvm/java-8-oracle
echo $JAVA_HOME
{% endhighlight %}