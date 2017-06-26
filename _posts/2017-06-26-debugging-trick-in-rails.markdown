---
layout: post
title:  "debugging trick in rails"
date:   2017-06-26 19:15:58 +0200
categories: development
---

when running your application in staging environment you can face some errors that you haven't experienced in dev environment.

for instance i was getting internal server error often.

go to your `staging.rb` file and make sure this value is set to true.
this will give you better rails-like error output instead of just internal server error.

{% highlight ruby %}
  config.consider_all_requests_local       = true
{% endhighlight %}  