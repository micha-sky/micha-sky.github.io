---
layout: post
title:  "mysql2 gem in ruby on rails 4"
date:   2016-03-05 13:57:58 +0200
categories: development
---

if you getting errors with your mysql gem in ruby on rails 4 you need to fix your Gemfile like this:
{%highlight ruby %}
gem 'mysql2' ~> '0.3.18'
{% endhighlight %}

this downgrades mysql2 gem to 0.3.18 version