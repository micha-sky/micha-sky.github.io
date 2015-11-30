---
layout: post
title:  "ftp server configuration on linux"
date:   2015-11-30 05:26:58 +0200
categories: development
---
quick note how to set up an ftp server on ubuntu. first you install vsftpd:

{% highlight console %}
sudo apt-get install vsftpd
{% endhighlight %}

then you edit configuration file with vim or nano or whatever you like
/etc/vsftpd.conf

{% highlight console %}
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
{% endhighlight %}