---
layout: post
title:  "ftp server configuration on amazon ec2"
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

then you need to add passive ports range to config file like this:

{% highlight console %}
pasv_min_port=8000
pasv_max_port=8100
{% endhighlight %}

also don't forget to open these port in amazon console's security group.