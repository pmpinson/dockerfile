Supported tags and respective Dockerfile links

* [5.0, latest](5.0/Dockerfile)


# Sonar
http://www.sonarqube.org/features/

# Build

`docker build --tag=pmpinson/sonarqube:5.0 .`

`docker build --tag=pmpinson/sonarqube .`

# Usage

`docker run -d --link some-mysql-container:db pmpinson/sonar`

must provide :
* link to mysql container : alias **db**, it must provide environnement variables **MYSQL_ROOT_PASSWORD**, **MYSQL_DATABASE**. You can use default [mysql container](../#mysql)

exposed port **9000**

volume **/app/conf**

volume **/app/logs**

volume **/app/plugins**

volume **/app/jdbc-driver**

default use for sonar is **admin**, password **admin**, you must change it.
