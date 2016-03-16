---
layout: post
title:  "method calling in ruby"
date:   2016-03-16 08:23:58 +0200
categories: development
---
there are three ways of calling method in ruby: dot operator, Object#send and method(:foo).call

{% highlight ruby %}
object = Object.new
object.object_id
=> 20826000
object.send(:object_id)
=> 20826000
object.method(:object_id).call
=> 20826000
{% endhighlight %}