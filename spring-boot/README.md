# Tags and links to `Dockerfile`

-	[`jdk8-onbuilld`, `latest`, (*jdk8-onbuilld/Dockerfile*)](jdk-8/Dockerfile)

Base image for apps [Spring Boot](http://projects.spring.io/spring-boot/).

This image uses instruction [ONBUILD](https://docs.docker.com/engine/reference/builder/#onbuild)

## What is Spring Boot?


Spring Boot makes it easy to create Spring-powered, production-grade applications and services with absolute minimum fuss. It takes an opinionated view of the Spring platform so that new and existing users can quickly get to the bits they need.
You can use Spring Boot to create stand-alone Java applications that can be started using java -jar or more traditional WAR deployments.
Reference guide [here](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/)


## How to use this Docker image:

* You need to create a child Dockerfile and indicate the jar/war path as "ENV". The env var "FILE" is required. If you need an entrypoint you can create it but entrypoint is not required:

```
FROM carlosamartins/spring-boot
ENV FILE target/app.jar
ENV ENTRYPOINT src/entrypoint.sh
```

* The entrypoint can be anything. Does not forget to put "exec $@" on the final:

```
#!/bin/bash

function export_var() {
  eval VAL=\$$2
  if [ ! -z $VAL ]; then
    if [ ! -z $3 ]; then
      VAL=$3
    fi
    export $1=$VAL
    echo "config per link: $1=$VAL"
  fi
}

export_var URL_WEBSERVICE CONTAINER1_PORT_8080_TCP_ADDR "http://$URL_WEBSERVICE CONTAINER1_PORT_8080_TCP_ADDR:8080/servicows"
export_var URL_ANOTHER_SERVICE CONTAINER2_PORT_8080_TCP_ADDR "http://$CONTAINER2_PORT_8080_TCP_ADDR:8080/services/Servico?wsdl"

exec $@
```

* Build app image:

```
docker build -t docker-web.softplan.com.br/unj/app-name /path/Dockerfile
```

* Run container:

```
docker run -it --env-file path/config.properties docker-web.softplan.com.br/unj/app-name
```


* The config.properties can be a file that contains the env vars as below:

```
TZ=America/Sao_Paulo
JAVA_OPTS=-Xrs -Duser.language=pt -Duser.country=BR -Duser.timezone=America/Sao_Paulo -Dfile.encoding=UTF-8
logging.path=/app/log
logging.level.root=WARN
spring.datasource.url=jdbc:mysql://localhost/test
spring.datasource.username=dbuser
spring.datasource.password=dbpass
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.max-wait=10000
spring.datasource.max-active=50
spring.datasource.test-on-borrow=true
```
