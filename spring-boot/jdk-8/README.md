# Tags e links para o `Dockerfile`

-	[`jdk8-onbuilld`, `latest`, (*jdk8-onbuilld/Dockerfile*)](jdk-8/Dockerfile)

Imagem base para aplicações em [Spring Boot](http://projects.spring.io/spring-boot/).

## O que é Spring Boot?


Spring Boot facilita a criação de aplicações java onde você pode criar aplicações independentes que podem ser iniciados usando "-jar java" com o mínimo de configuração possível. Documentação completa disponível aqui:
```
http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/
```

## Como utilizar essa imagem:

* Criar Dockerfile filho para a aplicação:

```
FROM docker-web.softplan.com.br/unj/spring-boot
ENV FILE target/app.jar
```

* Criar imagem da aplicação:

```
docker build -t docker-web.softplan.com.br/unj/app-name /path/Dockerfile
```

* Iniciar o container:

```
docker run -it --env-file path/config.properties docker-web.softplan.com.br/unj/app-name
```
