---
layout: post
title:  "running jenkins and glassfish on one instance"
date:   2015-12-04 01:39:58 +0200
categories: deployment
---
installing jenkins. sudo su before this

{% highlight console %}
wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | apt-key add -
echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list
{% endhighlight %}

{% highlight console %}
apt-get update
apt-get install jenkins
{% endhighlight %}

check your jenkins dashboard: yourserver.com:8080
Add admin user, uncheck “allow users to sign up”, configure matrix-based security, install git and bitbucket plugin.

now, let's download and install glassfish 4.1
{% highlight console %}
wget http://download.java.net/glassfish/4.1.1/release/glassfish-4.1.1.zip

sudo unzip glassfish-4.1.1.zip -d /opt
{% endhighlight %}

add glassfish to PATH variable
{% highlight console %}
export PATH=/opt/glassfish4/bin:$PATH
{% endhighlight %}

run test domain, and wait for it to start, and then stop it
{% highlight console %}
asadmin start-domain
asadmin stop-domain
{% endhighlight %}

now let's create our domain, and set admin user/password for it
{% highlight console %}
asadmin create-domain yourdomain
{% endhighlight %}

glassfish will choose random port, because jenkins already took 8080, so now we can run them together on one instance.

