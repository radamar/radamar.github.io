---
title: "Install and run 52°North Web Processing Service on Apache Tomcat server."
---

First you want to head over to the 52°North Github repository, [here][1]. Go through the README.md if you like.

The next part is to install the tools you will need to download and build the project from source. For Arch Linux:
{% highlight shell %}
pacman -S git maven
{% endhighlight %}

Install the dependencies as listed in the `README.md`.

{% highlight shell %}
pacman -S java-8-jdk tomcat8
{% endhighlight %}

Build the project using Apache maven build tool.

{% highlight shell %}
cd WPS
mvn clean install
{% endhighlight %}

Copy the built Web Application Resource(xyz.war) to tomcat autodeploy folder. 
{% highlight shell %}
cp 52n-wps-webapp/target/52n-wps-webapp-<VERSION>.war /var/lib/tomcat8/webapps/sample.war
{% endhighlight %}

open this link, [http://localhost:8080/sample][2] and try it out!

[1]: https://github.com/52North/WPS

[2]: http://localhost:8080/sample
