---
layout: post
title:  "csv manipulation with sed and awk"
date:   2016-07-08 08:23:58 +0200
categories: development
---
if you have huge file and you need to split it into pieces by 40MB
{% highlight console %} 
split --bytes 40M --numeric-suffixes --suffix-length=3 file.csv spl
{% endhighlight %}

split file by 150 lines with -l parameter. spl is prefix for split files
{% highlight console %} 
split --l 150 --numeric-suffixes --suffix-length=3 file.csv spl
{% endhighlight %}

count number o lines with wc command. -l indicates lines
{% highlight console %}
wc -l file.csv 
{% endhighlight %}

remove whitespace from file with sed 
{% highlight console %}
sed -i '/^$/d' file.csv
{% endhighlight %}

select columns 1-3 from file to newfile
{% highlight console %}
cut -d, -f1-3 file.csv > newfile.csv
{% endhighlight %}