docker-h2
=========

Dockerized H2 database service.


## Features

* Based on [the `OpenJDK` official image](https://hub.docker.com/r/_/openjdk/)
* H2-DATA location on `/opt/h2-data`
* A mix of [zhilvis/docker-h2](https://github.com/zhilvis/docker-h2) and [zilvinasu/h2-dockerfile](https://github.com/zilvinasu/h2-dockerfile).


## Trusted builds

[Automated builds](https://hub.docker.com/r/oscarfonts/h2/) on [docker registry](https://registry.hub.docker.com/):

* [`latest`, `1.4.199` (*1.4.199/Dockerfile*)](https://github.com/oscarfonts/docker-h2/blob/master/1.4.199/Dockerfile)
* [`alpine` (*alpine/Dockerfile*)](https://github.com/oscarfonts/docker-h2/blob/master/alpine/Dockerfile)
* [`1.1.119` (*1.1.119/Dockerfile*)](https://github.com/oscarfonts/docker-h2/blob/master/1.1.119/Dockerfile)
* [`geodb` (*geodb/Dockerfile*)](https://github.com/oscarfonts/docker-h2/blob/master/geodb/Dockerfile)


## Running

Get the image:

```
docker pull oscarfonts/h2
```

Run as a service, exposing ports 1521 (TCP database server) and 8081 (web interface) and mapping DATA_DIR to host:

```
docker run -d -p 1521:1521 -p 8081:8081 -v /path/to/local/data_dir:/opt/h2-data --name=MyH2Instance oscarfonts/h2
```

Or run as a service with an extra custom config set in the command line, like allowing to create database at connection:

```
docker run -d -p 1521:1521 -p 8081:8081 -v /path/to/local/data_dir:/opt/h2-data -e H2_OPTIONS=-ifNotExists --name=MyH2Instance oscarfonts/h2
```

The H2 web console will be available at: http://localhost:8081

See the logs while running:

```
docker logs -f MyH2Instance
```
