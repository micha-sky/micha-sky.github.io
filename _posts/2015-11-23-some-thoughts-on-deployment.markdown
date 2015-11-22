---
layout: post
title:  "some thoughts on deployment"
date:   2015-11-23 0135:58 +0200
---
i wonder if you need cargo plugin to deploy Java applicaton to
glassfish.

need to try adding this to my proejct.

{% highlight cmake %}

/usr/local/glassfish/bin/asadmin --echo=true --host=localhost --port=4848 --user=admin --passwordfile=/secure/place/for/passwords/domain1_password --secure=false deploy --force=true --name=myproject --contextroot=/myproject target/*.war

{% endhighlight %}

{% highlight xml %}

<build>
	<plugins>
		<plugin>
			<groupId>org.codehaus.cargo</groupId>
			<artifactId>cargo-maven2-plugin</artifactId>
			<version>1.3.3</version>
			<configuration>
				<container>
					<containerId>glassfish3x</containerId>
					<type>remote</type>
				</container>
				<configuration>
					<type>runtime</type>
					<properties>
						<cargo.hostname>localhost</cargo.hostname>
						<cargo.remote.username>admin</cargo.remote.username>
						<cargo.remote.password>admin</cargo.remote.password>
						<cargo.remote.port>50447</cargo.remote.port>
						<cargo.glassfish.domain.name>/myapp</cargo.glassfish.domain.name>
					</properties>
				</configuration>
				<deployables>
					<deployable>
						<groupId>${project.groupId}</groupId>
						<artifactId>${project.artifactId}</artifactId>
						<type>war</type>
						<properties>
							<context>/myapp</context>
						</properties>
					</deployable>
				</deployables>
			</configuration>
			<dependencies>
				<dependency>
					<groupId>org.glassfish.deployment</groupId>
					<artifactId>deployment-client</artifactId>
					<version>3.2-b06</version>
				</dependency>
			</dependencies>
		</plugin>
	</plugins>
</build>

{% endhighlight %}