![grafico_docker](https://upload.wikimedia.org/wikipedia/commons/7/79/Docker_%28container_engine%29_logo.png)

##Docker Basics: 
Run an image. 
```php
$ docker run [OPTIONS] IMAGE[:TAG] [COMMAND] [ARG...]
```
For instance, this command runs the echo command in the Ubuntu image:
```php
$ docker run ubuntu /bin/echo 'Hello world'

Hello world
```
Run an interactive container.
```php
$ docker run -t -i ubuntu /bin/bash

root@af8bae53bdd3:/#
```
-t flag means you want a terminal inside the new container.

-i flag allows you to make an interactive connection.

Create container that runs as a daemon.
```php
$ docker run -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done"

1e5535038e285177d5214659a068137486f96ee5c2e85a4ac52dc83f2ebe4147
```
List containers.
```php
$ docker ps

CONTAINER ID  IMAGE         COMMAND               CREATED        STATUS       PORTS NAMES
1e5535038e28  ubuntu  /bin/sh -c 'while tr  2 minutes ago  Up 1 minute        insane_babbage
```
Shows the standard output of a container.
```php
$ docker logs insane_babbage

hello world
hello world
hello world
. . .
```
Stop running containers.
```php
$ docker stop insane_babbage
insane_babbage
```

To add:
docker rm
docker images
docker rmi

