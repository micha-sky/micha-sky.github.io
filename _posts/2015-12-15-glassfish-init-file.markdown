---
layout: post
title:  "glassfish init script for linux"
date:   2015-12-15 19:39:58 +0200
categories: deployment
---

 glassfish init script for linux 

 create glassfish init file:
{% highlight console %}
sudo vi /etc/init.d/glassfish
{% endhighlight %}

{% highlight console %}
#!/bin/sh


GLASSFISH_HOME=${GLASSFISH_HOME:-"/opt/glassfish/glassfish4"}

case "$1" in
start)
$GLASSFISH_HOME/bin/asadmin --passwordfile pdwfile start-domain domainname>/dev/null
;;
stop)
$GLASSFISH_HOME/bin/asadmin --passwordfile pdwfile stop-domain domainname >/dev/null
;;
restart)
$GLASSFISH_HOME/bin/asadmin --passwordfile pdwfile restart-domain domainname>/dev/null
;;
\*)
echo "usage: $0 (start|stop|restart|help)"
esac
{% endhighlight %}

>/dev/null means that we redirect output to null device (simply hiding the ouput)

pwdfile is path your glassfish password file