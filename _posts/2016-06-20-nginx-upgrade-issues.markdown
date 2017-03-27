---
layout: post
title:  "nginx upgrade issues"
date:   2016-06-20 08:23:58 +0200
categories: development
---
if you upgrading to ubuntu 16

dpkg: error processing archive /var/cache/apt/archives/nginx-extras_1%3a1.10.1-8.5.0.29~trusty1_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/nginx', which is also in package nginx 1.11.2-1~trusty
 dpkg-deb: subprocess paste killed by signal (Broken pipe)


 sudo apt-get install -f

 sudo dpkg -i --force overwrite /var/cache/apt/archives/nginx-common_1%3a1.10.1-8.5.0.29~trusty1_all.deb
