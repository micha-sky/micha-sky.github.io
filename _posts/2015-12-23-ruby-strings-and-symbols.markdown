---
layout: post
title:  "ruby strings and symbols"
date:   2015-12-23 15:51:23 +0200
categories: development
---
i want to explain the difference between strings and symbols in ruby.
strings are surrounded by single or double quotes, symbols starts with colon.

strings are equal 
{% highlight ruby %}
"hello" == 'hello'
=> true

:hello == :hello
=> true
{% endhighlight %}

but string and symbol aren't
{% highlight ruby %}
"hello" == :hello
=> false
{% endhighlight %}

the other thing is that strings are mutable objects but symbols aren't. also each string has its own place in memory allocated. symbols share same space in heap
