# Supported tags and respective `Dockerfile` links

-       [`2.11-jdk8`, `latest` (*2.11/Dockerfile*)](https://github.com/carlosamartins/Dockerfiles/blob/master/gradle/jdk-8/2.11/Dockerfile)
-       [`2.11-jdk8-alpine` (*alpine/2.11/Dockerfile*)](https://github.com/carlosamartins/Dockerfiles/blob/master/gradle/alpine/jdk-8/2.11/Dockerfile)

# What is Gradle?

Gradle is an open source build automation system that builds upon the concepts of Apache Ant and Apache Maven and introduces a Groovy-based domain-specific language (DSL) instead of the XML form used by Apache Maven of declaring the project configuration. Gradle uses a directed acyclic graph ("DAG") to determine the order in which tasks can be run.

Learn more on [Gradle homepage](http://gradle.org/) and in the [Gradle Reference Guide](https://docs.gradle.org/current/userguide/userguide.html).


# How to use this Docker image

To run a Gradle with Docker command:

```console
$ docker run --rm -v $HOME/.m2:/gradle/.m2 -v $HOME/myapp:/app carlosamartins/gradle build
```

# License

View license information for the software contained in this image.

# Supported Docker versions

This image is officially supported on Docker version 1.9.1.

Support for older versions (down to 1.0) is provided on a best-effort basis.

## Issues

Please report issues with this docker image on this [Github project](https://github.com/carlosamartins/Dockerfiles).
