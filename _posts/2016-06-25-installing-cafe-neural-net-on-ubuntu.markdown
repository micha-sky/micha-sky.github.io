---
layout: post
title:  "installing caffe neural net on ubuntu"
date:   2016-06-25 07:05:58 +0200
categories: development
---
if you want to use google's deep dream you surely need to install caffe deep learning framework

i won't describe cloning caffe from github (duh) so let's get going


i assume we won't use CUDA (it's a whole new story) so you need to make following changes in Makefile.config.example 

{% highlight console %}
CPU_ONLY := 1

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
{% endhighlight %}

then 
{% highlight console %}
make all
make test
make runtest
{% endhighlight %}

you may want to add -j 4 to those commands to run run in 4 or whatever parallel threads you want to run

also important
{% highlight console %}
export PYTHONPATH=/home/username/caffe/python
{% endhighlight %}
