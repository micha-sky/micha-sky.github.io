---
layout: post
title:  "how to center a div"
date:   2016-11-24 11:24:58 +0200
categories: development
---

![image1](/assets/css.png){:class="img-responsive"}

the funniest thing is that it's ablolutely true

{% highlight css %}
.parent {
  position: relative;
}
{% endhighlight %}

{% highlight css %}
.child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
{% endhighlight %}
