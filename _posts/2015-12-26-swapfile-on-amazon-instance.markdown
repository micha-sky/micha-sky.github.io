---
layout: post
title:  "swapfile on amazon instance"
date:   2015-12-26 10:55:23 +0200
categories: deployment
---
amazon ec2 instance doesn't have swapfile by default:
{% highlight console %}
sudo swapon -s
{% endhighlight %}
the output should show no swap files. we need to add a swap file for better instance performance.

we can create a 4gb file by typing:

{% highlight console %}
sudo fallocate -l 4G /swapfile
{% endhighlight %}

now we need to set permissions to file, so only root can write to it.
{% highlight console %}
sudo chmod 600 /swapfile
{% endhighlight %}

now let's make a swap
{% highlight console %}
sudo mkswap /swapfile
{% endhighlight %}

finally we need to enable a swap file 
{% highlight console %}
sudo swapon -s
{% endhighlight %}

now the output of >sudo swapon -s 
will show that you have a 4gb swap file.