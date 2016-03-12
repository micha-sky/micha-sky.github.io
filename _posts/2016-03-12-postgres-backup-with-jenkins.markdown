---
layout: post
title:  "manage postgres backups with jenkins"
date:   2016-03-12 11:19:58 +0200
categories: development
---

with jenkins you can use it also for backing up your postgres database scheduled with cron.

i assume you have jenkins user in system.
login as user postgres and go to psql console:
create user jenkins in psql:
{%highlight sql %}
create user jenkins;
{% endhighlight %}

now we need to grant permissions for this user:
{%highlight sql %}
GRANT SELECT ON ALL TABLES IN SCHEMA public TO jenkins;

GRANT CONNECT ON DATABASE yourdatabase to jenkins;
\c yourdatabase
GRANT USAGE ON SCHEMA public to jenkins;

GRANT SELECT ON ALL SEQUENCES IN SCHEMA public TO jenkins;

GRANT SELECT ON ALL TABLES IN SCHEMA public TO jenkins;
{% endhighlight %}