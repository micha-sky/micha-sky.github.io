---
layout: post
title:  "setting up mail server on ubuntu using postfix"
date:   2016-02-21 15:13:23 +0200
categories: deployment
---
lets all the things we need for mailing
{% highlight console %}
sudo apt-get install postfix mailutils courier-pop courier-imap
{% endhighlight %}

don't forget to open necessary ports if you running on amazon (25, 143, POP, IMAP)

