## docker-registry-fig-mirror

This project is a fig harness to manage a docker-registry acting as a caching mirror.

First, go read the [official docker registry_mirror page](https://github.com/docker/docker/blob/master/docs/sources/articles/registry_mirror.md), and come back here.

This fig.yml assumes a local host filesystem of /docker-registry is ready to be used for the docker registry mirroed cache persistence.

This has a sqlite enabled sqlalchemy search index, as well as a redis LRU cache for smaller files to avoid hitting disk when possible.

You will need to point your slave docker daemons at this docker host as a registry-mirror on port 5000 to use this cache:

    docker -d --registry-mirror http://{ip}:5000 --insecure-registry 10.0.0.0/8 --insecure-registry 172.16.0.0/12 --insecure-registry 192.168.0.0/16

