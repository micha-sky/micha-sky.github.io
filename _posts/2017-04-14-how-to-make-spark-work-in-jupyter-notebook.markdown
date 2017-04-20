---
layout: post
title:  "how to make spark work in jupyter notebook"
date:   2017-04-14 11:24:58 +0200
categories: development
---

how to make spark work in jupyter notebook

{% highlight console %}
export PYTHONPATH=$SPARK_HOME/python/:$PYTHONPATH
export PYTHONPATH=$SPARK_HOME/python/lib/py4j-0.10.3-src.zip:$PYTHONPATH
{% endhighlight %}