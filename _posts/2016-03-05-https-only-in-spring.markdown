---
layout: post
title:  "https in spring application"
date:   2016-03-05 13:57:58 +0200
categories: development
---

if you want to use only https connection you have to add following security to your web.xml file:

{% highlight xml %}
<security-constraint>
        <web-resource-collection>
            <web-resource-name>YourApplication</web-resource-name>
            <url-pattern>/*</url-pattern>
            <http-method>GET</http-method>
        </web-resource-collection>
        <user-data-constraint>
            <transport-guarantee>CONFIDENTIAL</transport-guarantee>
        </user-data-constraint>
    </security-constraint>
{% endhighlight %}