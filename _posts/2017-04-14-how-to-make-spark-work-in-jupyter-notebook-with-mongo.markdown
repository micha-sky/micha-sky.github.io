---
layout: post
title:  "how to make spark work with mongodb in jupyter notebook"
date:   2017-04-18 17:24:58 +0200
categories: development
---

how to make spark work with mongodb

{% highlight console %}
git clone https://github.com/mongodb/mongo-spark.git
./sbt check
./sbt +publish-signed


pyspark --conf "spark.mongodb.input.uri=mongodb://127.0.0.1/switch.KN?readPreference=primaryPreferred"               --conf "spark.mongodb.output.uri=mongodb://127.0.0.1/switch.KN"               --packages org.mongodb.spark:mongo-spark-connector_2.11:2.0.0
{% endhighlight %}

df = spark.read.format("com.mongodb.spark.sql.DefaultSource").load()
df.show()


database = 'switch'
collection = 'KN'
df2 = spark.read.format("com.mongodb.spark.sql.DefaultSource").option("uri", "mongodb://127.0.0.1/{database}.{collection}").load()


export PACKAGES="org.mongodb.spark:mongo-spark-connector_2.11:2.0.0"
export PYSPARK_SUBMIT_ARGS="--packages ${PACKAGES} pyspark-shell"
