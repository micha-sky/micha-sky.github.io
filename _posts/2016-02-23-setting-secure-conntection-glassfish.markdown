---
layout: post
title:  "setting up secure connection of glassfish"
date:   2016-02-23 13:13:23 +0200
categories: deployment
---
before setting up ssl certificates i assume you have yor domain set set up, also glassfish master password and admin passwords. thats how you get an access to keystore files.

run following commands to list your certificates
{% highlight console %}
keytool -list -v -keystore /opt/glassfish3/glassfish/domains/yourdomain/config/keystore.jks 

keytool -list -v -keystore /opt/glassfish3/glassfish/domains/yourdomain/config/cacerst.jks 
{% endhighlight %}

now we need to delete default certificates called s1as and glassfish instance from keystore.jks and cacerts.jks
{% highlight console %}
keytool -delete -alias s1as -keystore keystore.jks
keytool -delete -alias glassfish-instance -keystore keystore.jks

keytool -delete -alias s1as -keystore cacerts.jks
keytool -delete -alias glassfish-instance -keystore keystore.jks
{% endhighlight %}

now let's generate keypairs and update our keystores
{% highlight console %}
keytool -genkeypair -alias s1as -dname "CN=test.control-delivery.com.ua,OU=IT,O=Apitect,L=Kiev,S=Kiev,C=UA" -keyalg RSA -keysize 2048 -validity 3650 -keystore keystore.jks -keypass myMasterPwd -storepass myMasterPwd

keytool -genkeypair -alias glassfish-instance -dname "CN=serverDomainName,OU=someUnit,O=someOrg,L=someCity,S=someState,C=XX" -keyalg RSA -keysize 2048 -validity 3650 -keystore keystore.jks -keypass myMasterPwd -storepass myMasterPwd

keytool -exportcert -alias s1as -file s1as.cert -keystore keystore.jks 
keytool -exportcert -alias glassfish-instance -file glassfish-instance.cert -keystore keystore.jks
{% endhighlight %}

now let's import certificates to keystores. type 'yes' when asked if trust certificates
{% highlight console %}
keytool -importcert -alias s1as -file s1as.cert -keystore cacerts.jks
keytool -importcert -alias glassfish-instance -file glassfish-instance.cert -keystore cacerts.jks
{% endhighlight %}

also don't forget to change http-listener port to 443 (default https port)
now restart your domain to apply changes.


for the more info check out this blog http://www.brain-dynamics.net/~chris_rennie/glassfish.html


if you using comodo certificates you need to do following stuff:

concatenate certificates into a bundle
{% highlight console %}
cat domain_com.crt domain_com.ca-bundle > ssl-bundle.crt
{% endhighlight %}

import bundle certificate into keystore

{% highlight console %}
keytool -import -trustcacerts -alias root_alias_name -file bundle.crt -keystore cacerts.jks
{% endhighlight %}

type 'yes' to accept it

important thing: create a p12 file
{% highlight console %}
openssl pkcs12 -export -in bundle.crt -inkey mydomain.key -out mydomain.p12 -name mydomain_alias_name
{% endhighlight %}

where mydomain.key is an output from 'certreq' command.

now import p12 file into keystore

{% highlight console %}
keytool -importkeystore -deststorepass masterpassword -destkeypass masterpassword -destkeystore keystore.jks   -srckeystore mydomain.p12 -srcstoretype PKCS12 -srcstorepass masterpassword -alias mydomain_alias_name
{% endhighlight %}

now restart glassfish, and don't forget to set up http listeners in glassfish for new certificate alias.