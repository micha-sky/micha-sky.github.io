---
layout: post
title:  "glassfish response headers"
date:   2016-03-15 07:55:58 +0200
categories: development
---
i recently noticed that by deafault glassfish returns some interesing headers with every response.
try this out:

{% highlight console %}
curl -I yourdomain.com

HTTP/1.1 405 Request method &#39;HEAD&#39; not supported
Server: GlassFish Server Open Source Edition  4.1.1 
X-Powered-By: Servlet/3.1 JSP/2.3 (GlassFish Server Open Source Edition  4.1.1  Java/Oracle Corporation/1.8)
Allow: GET
Content-Length: 1214
Content-Language: 
Content-Type: text/html;charset=UTF-8
Date: Tue, 15 Mar 2016 05:49:05 GMT

{% endhighlight %}

if you don't find these headers neccesary (neither do i) you can disable with
{% highlight console %}
asadmin set server.network-config.protocols.protocol.http-listener-1.http.xpowered-by=false 
{% endhighlight %}

or in glassfish web interface.

this leaves out server header. to replace it we need to create jvm option called "product name"

{% highlight console %}
asadmin create-jvm-options -Dproduct.name="MyProduct"
{% endhighlight %}

or in web interface.
don't forget to restart your domain. 