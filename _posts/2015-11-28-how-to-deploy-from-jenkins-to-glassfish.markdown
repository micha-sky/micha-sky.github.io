---
layout: post
title:  "how to set up jenkins project with glassfish"
date:   2015-11-28 00:39:58 +0200
categories: deployment
---
if you want to use jenkins and glassfish on one instance, it's very easy to for continious integration.

first you want to add new maven project and configure git repository. 

then you need to add pre-build script that pulls changes from repository:

{% highlight cmake %}
#!/bin/bash

cd /path/to/repository

git pull origin master
{% endhighlight %}

then you specify maven goal, e.g. 

{% highlight cmake %}
mvn clean package -DskipTests=true
{% endhighlight %}

after that you add post-build script, which deploys build to :

{% highlight cmake %}
#!/bin/bash

echo -n "Undeploying current version..."
/opt/glassfish4/bin/asadmin undeploy ROOT
echo "done"

echo -n "Stopping glassfish..."
/opt/glassfish4/bin/asadmin stop-domain yourdomain
echo "done"

echo -n "Starting glassfish..."
/opt/glassfish4/bin/asadmin start-domain yourdomain
echo "done"

echo -n "Deploying ROOT.WAR..."
/opt/glassfish4/bin/asadmin --user admin deploy --contextroot / --name ROOT /var/lib/jenkins/workspace/projectname/target/ROOT.war
echo "done"
{% endhighlight %}

aslo you want to use --passwordfile option, that allows you not to type password every time you run this script.
passwordfile contains AS_ADMIN_PASSWORD=yourpassword

this would probably work without stopping and starting domain.

after setting up project you want to build it, and schedule your build.