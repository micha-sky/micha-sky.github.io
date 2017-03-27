---
layout: post
title:  "event triggers in ubuntu"
date:   2016-07-01 10:58:58 +0200
categories: development
---
if you need to run scripts based on file creation or deletion or whatever you will use inoify interface in linux.

the tool i use is incron it allows to watch the directory and run scripts based on event

to install in type
{% highlight console %}
sudo apt-get install incron
{% endhighlight %}

after that you need to create tables for user

to install in type
{% highlight console %}
sudo vi /etc/incron.allow
{% endhighlight %}

and add user root and save it. this means root user can use crontab.

to access cronab just type 
{% highlight console %}
sudo incrontab -e
{% endhighlight %}

it is similar to cron, so you can type -r to remove table or -l to list jobs.

the basic patter is
{% highlight console %}
<PATH> <EVENT> ACTION 
{% endhighlight %}

events are:

IN_ACCESS           File was accessed (read) (*)

IN_ATTRIB           Metadata changed (permissions, timestamps, extended attributes, etc.) (*)

IN_CLOSE_WRITE      File opened for writing was closed (*)

IN_CLOSE_NOWRITE    File not opened for writing was closed (*)

IN_CREATE           File/directory created in watched directory (*)
IN_DELETE           File/directory deleted from watched directory (*)
IN_DELETE_SELF           Watched file/directory was itself deleted
IN_MODIFY           File was modified (*)
IN_MOVE_SELF        Watched file/directory was itself moved
IN_MOVED_FROM       File moved out of watched directory (*)
IN_MOVED_TO         File moved into watched directory (*)
IN_OPEN             File was opened (*)

wildcards are used to pass filename to script:

$$   dollar sign
$@   watched filesystem path (see above)
$#   event-related file name
$%   event flags (textually)
$&   event flags (numerically)


all logs are written lo /var/log/syslog