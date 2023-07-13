# Tomcat

This small project holds all the necessary files and commands to run Tomcat locally. Tomcat official documentation [link](https://tomcat.apache.org/).

## What inside?

1. The file `content.xml` removes the restriction for localhost for the `manager` app.
1. The file `tomcat-users.xml` creates user `tomcat` and adds the role `manager-gui` for the `manager` app.

## Pre requisite:

Installed Docker.

## How to run Tomcat locally

Open the terminal and run the next command:

 
```
docker run --name tomcat -it --rm -p 8080:8080 -v ./tomcat-users.xml:/usr/local/tomcat/conf/tomcat-users.xml -v ./context.xml:/tmp/context.xml tomcat:10.1 /bin/bash -c "mv /usr/local/tomcat/webapps /usr/local/tomcat/webapps2; mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps; cp /tmp/context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml; catalina.sh run"
```

> This fancy docker command does next things:
> 1. Adds `tomcat-users.xml`
> 1. Copies all default apps (including the `manager` app) to `webapps` folder.
> 1. Copies `context.xml` to `manager` app.
> 1. And runs Tomcat

Then open in browser: [http://localhost:8080/manager/html](http://localhost:8080/manager/html)

Credentials:
> user: `tomcat`

> password: `s3cret`


## Test section

Something about testing
