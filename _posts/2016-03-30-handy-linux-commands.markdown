---
layout: post
title:  "handy linux commands"
date:   2016-03-30 13:33:58 +0200
categories: development
---

prints file sizes in megabytes
{% highlight console %}
ls -l --block-size=M
{% endhighlight %}

counts files in directory
{% highlight console %}
ls -1 | wc -l
{% endhighlight %}

sorts files by time (-tr to reverse order)
{% highlight console %}
ls -t -l
{% endhighlight %}

sorts files by size (-Sr to reverse)
{% highlight console %}
ls -S -l
{% endhighlight %}

find files containig text
{% highlight console %}
grep -r TEXT *
{% endhighlight %}

if you want to download a list of files
{% highlight console %}
wget -i <urls class="txt"></urls>
{% endhighlight %}

add prefix to all .csv files in directory
{%highlight console %}
for file in *.csv; do   mv "$file" "preix_${file}"; done
{% endhighlight %}


upgrade all pip packages (caraful may beak some versions dependencies)
{%highlight console %}
pip freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 sudo pip install -U
{% endhighlight %}

copy file contents to clipboard
{%highlight console %}
cat ~/.ssh/id_rsa | xclip -sel clip
{% endhighlight %}
