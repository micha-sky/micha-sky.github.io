---
layout: post
title:  "handy linux commands"
date:   2016-03-30 13:33:58 +0200
categories: development
---

prints file sizes in megabytes
{% highlight console %}
ls -l --block-size=M
{% endhighlight %}

counts files in directory
{% highlight console %}
ls -1 | wc -l
{% endhighlight %}

sorts files by time (-tr to reverse order)
{% highlight console %}
ls -t -l
{% endhighlight %}

sorts files by size (-Sr to reverse)
{% highlight console %}
ls -S -l
{% endhighlight %}
