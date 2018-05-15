---
layout: post
title:  "automating jmeter tests"
date:   2018-05-11 11:17:58 +0200
categories: development, testing
---

if you have jmeter tests in you project and bothered of running them all the time manually you can run following command:

{% highlight console %}

    jmeter -n -t file.jmx -l "report.csv"

{% endhighlight %}

this will run jmeter test in background and save report in csv format.

{% highlight console %}

#!/usr/bin/env bash

for file in test/*.jmx; do
    [ -e "$file" ] || continue
    jmeter -n -t "$file" -l "reports/report.csv" |  grep -E --color '\d{1,2}\.\d{1,2}|$'
done
{% endhighlight %}