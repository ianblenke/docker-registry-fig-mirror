## docker-registry-fig-mirror

This project is a fig harness to manage a docker-registry acting as a cache.

The fig.yml assumes a local host filesystem of /docker-registry is ready to be used for the docker registry cache.

You will need to point your slave docker daemons at this docker host as a registry-mirror on port 5000 to use this cache:

    docker -d --registry-mirror {ip}:5000 --insecure-registry 10.0.0.0/8 --insecure-registry 172.16.0.0/12 --insecure-registry 192.168.0.0/16

