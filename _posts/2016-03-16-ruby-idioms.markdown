---
layout: post
title:  "ruby idioms"
date:   2016-03-16 09:33:58 +0200
categories: development
---
unless works like if not

until is while not

swap values: x, y = y, x

__FILE__ - name of current source file
{% highlight ruby %}
irb(main):024:0> puts __FILE__
(irb)
{% endhighlight %}

$0 - name of top level program executed
{% highlight ruby %}
irb(main):024:0> puts $0
irb
=> nil
{% endhighlight %}

$: is array of paths

$! is current exeption raised. nil if no exeption being raised

$SAFE is current safe level

ENV is hash of environment vairables

methods ending wiht '?' are boolean
{% highlight ruby %}
puts ('ok') if File.exists?('filename')
{% endhighlight %}

methods ending wiht '!' modify current object
{% highlight ruby %}
str = "   hello world   "
str.strip!
p str   # -> "hello world"
{% endhighlight %}

||= or-equal operator 
a ||= b means assign b to a if a is nil or false
{% highlight ruby %}
a = nil
b = 2
a ||= b
=> 2
{% endhighlight %}

ruby's getters and setters are attr_reader, attr_writer and attr_accessor
{% highlight ruby %}
class Awesome
	attr_accessor: :name, :date
end
{% endhighlight %}

ruby's analog to try-catch-finally is begin-rescue-ensure

== operator checks if two ojects are equal
.eql?  check if objects types and values are equal
.equal? checks if two object are the same object

{% highlight ruby %}
1 == 1.0
=> true

1.eql?(1.0)
=> false

{% endhighlight %}