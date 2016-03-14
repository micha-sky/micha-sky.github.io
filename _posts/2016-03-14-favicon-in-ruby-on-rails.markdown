---
layout: post
title:  "favicon in ruby on rails 4"
date:   2016-03-14 16:46:58 +0200
categories: development
---
if you need to add favicon to your ror application 
{% highlight ruby %}
= favicon_link_tag 'favicon.png'
{% endhighlight %}

favicon.png should be located in your assets/images/ directory.