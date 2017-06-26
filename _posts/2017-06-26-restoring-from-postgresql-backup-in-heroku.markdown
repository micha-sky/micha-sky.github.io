---
layout: post
title:  "restoring from postgresql backup in heroku"
date:   2017-06-26 18:47:58 +0200
categories: development
---

heroku is a very convenient service (no doubt).

i will tell you a little one liner trick that helps you restore from your pg backup.


i assume that you know heroku basics and already have heroku cli installed.

you can use heroku tutorial on restoring but it didn't work for me


{% highlight console %}
heroku pg:psql --app YOU_APP_NAME < backup.sql 
{% endhighlight %}

this will run restore command.