---
layout: post
title:  "setting up nginx with spring boot"
date:   2017-08-17 22:44:58 +0200
categories: development
---

run you spring boot app as a service packed to jar file.
it will start tomcat server at port 8080.


create a config in /etc/nginx/sites-available for your app:

{% highlight console %}
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                proxy_pass http://domain.com:8080/;
                proxy_set_header Host $host;
                proxy_set_header X-Read-IP $remote_addr;
                try_files $uri $uri/ =404;
        }

        location ~* \.(svg|js|jpg|png|css|html|gif|pdf|woff|ttf)$ {
            proxy_pass              $scheme://domain.com:8080/$request_uri;
            proxy_redirect  off;
            proxy_set_header        X-Real-IP $remote_addr;
            proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header        Host $http_host;
            expires 30d;
    }

}
{% endhighlihgt %}

