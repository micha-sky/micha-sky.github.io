---
layout: post
title:  "postman and its' certificates"
date:   2018-05-15 16:15:58 +0200
categories: development
---

for some reason postman deceided to release a standalone app and deprecate chrome app.

that's cool but chrome app has no problem using certificates. this one does.

solution provided by github user [@davefuentes](https://github.com/postmanlabs/postman-app-support/issues/2494#issuecomment-281854887)

basically you need to convert your PFX / P12 certificate to crt + key pair and disable ssl verification.

neat right?

