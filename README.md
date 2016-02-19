# Supported tags and respective `Dockerfile` links

-       [`4.4.0`, `latest` (*4.4/Dockerfile*)](https://github.com/carlosamartins/Dockerfiles/blob/master/4.4.0/Dockerfile)

For more information about this image and its history, please see [the relevant manifest file (`library/solr`)](https://github.com/docker-library/official-images/blob/master/library/solr). This image is updated via pull requests to [the `docker-solr/docker-solr` GitHub repo](https://github.com/docker-solr/docker-solr).

For detailed information about the virtual/transfer sizes and individual layers of each of the above supported tags, please see [the `solr/tag-details.md` file](https://github.com/docker-library/docs/blob/master/solr/tag-details.md) in [the `docker-library/docs` GitHub repo](https://github.com/docker-library/docs).

# What is Solr?

Solr is highly reliable, scalable and fault tolerant, providing distributed indexing, replication and load-balanced querying, automated failover and recovery, centralized configuration and more. Solr powers the search and navigation features of many of the world's largest internet sites.

Learn more on [Apache Solr homepage](http://lucene.apache.org/solr/) and in the [Apache Solr Reference Guide](https://www.apache.org/dyn/closer.cgi/lucene/solr/ref-guide/).

> [wikipedia.org/wiki/Apache_Solr](https://en.wikipedia.org/wiki/Apache_Solr)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/solr/logo.png)

# How to use this Docker image

To run a single Solr server:

```console
$ docker run --name my_solr -d -p 8983:8983 -t solr
```

Then with a web browser go to `http://localhost:8983/` to see the Admin Console (adjust the hostname for your docker host).

To use Solr, you need to create a "core", an index for your data. For example:

```console
$ docker exec -it --user=solr my_solr bin/solr create_core -c gettingstarted
```

In the web UI if you click on "Core Admin" you should now see the "gettingstarted" core.

If you want to load some example data:

```console
$ docker exec -it --user=solr my_solr bin/post -c gettingstarted example/exampledocs/manufacturers.xml
```

In the UI, find the "Core selector" popup menu and select the "gettingstarted" core, then select the "Query" menu item. This gives you a default search for "*:*" which returns all docs. Hit the "Execute Query" button, and you should see a few docs with data. Congratulations!

To learn more about Solr, see the [Apache Solr Reference Guide](https://cwiki.apache.org/confluence/display/solr/Apache+Solr+Reference+Guide).

## Distributed Solr

You can also run a distributed Solr configuration.

The recommended and most flexible way to do that is to use Docker networking.
See the [Can I run ZooKeeper and Solr clusters under Docker](https://github.com/docker-solr/docker-solr/blob/master/Docker-FAQ.md#can-i-run-zookeeper-and-solr-clusters-under-docker) FAQ,
and [this example](docs/docker-networking.md).

You can also use legacy links, see the [Can I run ZooKeeper and Solr with Docker Links](Docker-FAQ.md#can-i-run-zookeeper-and-solr-clusters-under-docker) FAQ.

# What are the differences between this image and library/solr?

Uses root user by default instead solr user.
Adds Groovy script language tools.

# License

View license information for the software contained in this image.

# Supported Docker versions

This image is officially supported on Docker version 1.9.1.

Support for older versions (down to 1.0) is provided on a best-effort basis.

## Issues

Please report issues with this docker image on this [Github project](https://github.com/carlosamartins/Dockerfiles).
