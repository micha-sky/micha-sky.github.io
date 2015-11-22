---
layout: post
title:  "first Jekyll post"
date:   2015-11-23 00:54:58 +0200
categories: jekyll update
---
Not much, just trying out Jekyll.

This thing highlights code which is very cool.

{% highlight ruby %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}