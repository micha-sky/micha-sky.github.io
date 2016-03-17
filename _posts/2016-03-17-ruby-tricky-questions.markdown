---
layout: post
title:  "ruby tricky questions"
date:   2016-03-17 15:33:23 +0200
categories: development
---

here's some tricky questions i got on interviews

difference between Date.today & Date.current
{% highlight ruby %}
# Returns Time.zone.today when <tt>Time.zone</tt> or <tt>config.time_zone</tt> are     set, otherwise just returns Date.today.
  def current
    ::Time.zone ? ::Time.zone.today : ::Date.today
  end
{% endhighlight %}

difference between save & save!
save! will raise an error if not successful
save will return true or fase

difference between find and find_by
find will raise an error
find_by will return nil if not founds