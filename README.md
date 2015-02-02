# generality

this project presents some informations on docker https://www.docker.com/

# blogs

http://jonathan.bergknoff.com/journal/building-good-docker-images

# ui tool for docker management

https://github.com/crosbymichael/dockerui

`docker run -d -p 9005:9000 --privileged -v /var/run/docker.sock:/var/run/docker.sock dockerui/dockerui`

exposed port **9000**

# mongodb

https://registry.hub.docker.com/_/mongo/ 

`docker run -d mongo`

exposed port **27017**

volume **/data/db**

can connect to the server with other container

`docker run -it --link name-mongo-container:mongo --rm mongo sh -c 'exec mongo "$MONGO_PORT_27017_TCP_ADDR:$MONGO_PORT_27017_TCP_PORT/some-db"'`

# mysql
https://registry.hub.docker.com/_/mysql/

`docker run -d -p 9003:3306 -e MYSQL_ROOT_PASSWORD=mysecretpassword -e MYSQL_DATABASE=sonar mysql`

need to provide
* root password environnement variable **MYSQL_ROOT_PASSWORD**

can provide
* initiale database **MYSQL_DATABASE**
* specific username and password for this database **MYSQL_USER** and **MYSQL_PASSWORD**

exposed port **3306**

volume **/var/lib/mysql**

can connect to the server with other container

`docker run -it --link name-mysql-container:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'`

# sonarqube

docker container to provide a sonarqube server [see details](sonarqube).

# jenkins

docker container to provide a jenkins server [see details](jenkins).
