```
---
layout: post
title:  "install and use postgresql on linux"
date:   2015-12-05 06:54:58 +0200
categories: deployment
---
```

first we install postgresql:
{% highlight console %}
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
{% endhighlight %}

then, lets set password for postgres user:
{% highlight console %}
sudo su postgres
psql
\password postgres
{% endhighlight %}

after typing password exit the console. 
\q

now lets create a database. you can do it in PSQL console, but i prefer createdb utility:

{% highlight console %}
createdb -h localhost -p 5432 -U postgres yourdatabasename
{% endhighlight %}

where -h is host, -p is port and -U is user.