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

to connect spark to mongo db setup mongo connector:
{% highlight console %}
git clone https://github.com/mongodb/mongo-spark.git
./sbt check
./sbt +publish-signed
{% endhighlight %}


add this variables before running it in notebook
{% highlight console %}
export PACKAGES="org.mongodb.spark:mongo-spark-connector_2.11:2.0.0"
export PYSPARK_SUBMIT_ARGS="--packages ${PACKAGES} pyspark-shell"
{% endhighlight %}
