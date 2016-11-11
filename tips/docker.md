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
Create a container and map ports.
```php
docker run -d -P training/webapp python app.py

```
The -P flag maps any required network ports inside the container to your host. Using the -p flag you can map specific ports. For instance, to map port 5000 inside your container to port 80 on your local host:
```php
$ docker run -d -p 80:5000 training/webapp python app.py
```

List containers.
```php
$ docker ps -l

CONTAINER ID  IMAGE                   COMMAND       CREATED        STATUS        PORTS                    NAMES
bc533791f3f5  training/webapp:latest  python app.py 5 seconds ago  Up 2 seconds  0.0.0.0:49155->5000/tcp  nostalgic_morse
```
Shows the standard output of a container.
```php
$ docker logs -f nostalgic_morse

* Running on http://0.0.0.0:5000/
10.0.2.2 - - [06/Nov/2016 20:16:31] "GET / HTTP/1.1" 200 -
10.0.2.2 - - [06/Nov/2016 20:16:31] "GET /favicon.ico HTTP/1.1" 404 -
```
Inspect container.
```php
$ docker inspect nostalgic_morse
```
It will show a JSON document in the output containing useful configuration and status information for the specified container

Stop/start running containers.
```php
$ docker stop|start nostalgic_morse
nostalgic_morse
```
Remove container.
```php
$ docker rm nostalgic_morse

nostalgic_morse
```
Remove all containers.
```php
docker rm $(docker ps -aq)
```
