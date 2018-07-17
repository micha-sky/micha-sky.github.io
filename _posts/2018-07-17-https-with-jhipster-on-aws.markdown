---
published: false
---
## A New Post

## Using jHipster on AWS Elastic Beanstalk

Do the `jhipster aws` to deploy applicaiton to Elastic Beanstalk

By default you will get Load Balancer with listener to HTTP protocol port 80

If you want to enable HTTPS with Amazon issued certificate - you don't have to change anything in your applicaiton, no need of manipulation with `keytool` and so on.

You simply request a certificate, add a HTTPS listener, choose issued certificate and point it to HTTP port of you application (8080)

