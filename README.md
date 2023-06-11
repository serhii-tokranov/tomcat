# How to run Tomcat locally
Verify that `tomcat-users.xml` and `context.xml` exist and are configured correctly, then execute: 
```
docker run --name tomcat -it --rm -p 8080:8080 -v ./tomcat-users.xml:/usr/local/tomcat/conf/tomcat-users.xml -v ./context.xml:/tmp/context.xml tomcat:9.0 /bin/bash -c "mv /usr/local/tomcat/webapps /usr/local/tomcat/webapps2; mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps; cp /tmp/context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml; catalina.sh run"
```
and 
```
http://localhost:8080/manager/html
```