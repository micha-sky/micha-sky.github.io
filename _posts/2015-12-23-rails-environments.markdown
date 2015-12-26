---
layout: post
title:  "rails environments"
date:   2015-12-23 18:40:23 +0200
categories: development
---
rails has 3 environments by default: test, development and production. they have
corresponding configuration file in config/environments/ folder.   

test environment is used for testing application and has special database that is being wiped out between tests.

development mode turns off caching and reloads all classes for faster development.

in production cache is turned on the way it runs on live server.

the major convenience is that you can choose to run your code differently in different environments like this:

{% highlight ruby %}
if Rails.env.production?
# do stuff
elsif Rails.env.development
# do something else
end
{% endhighlight %}