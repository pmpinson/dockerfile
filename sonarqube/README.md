Supported tags and respective Dockerfile links

* [4.5.2, latest](4.5.2/Dockerfile)


# Sonar
http://www.sonarqube.org/features/

# Build

`docker build --tag=pmpinson/sonarqube:4.5.2 .`

`docker build --tag=pmpinson/sonarqube .`

# Usage

`docker run -d --link some-mysql-container:db pmpinson/sonar`

must provide :
* link to mysql container : alias **db**, it must provide environnement variables **MYSQL_ROOT_PASSWORD**, **MYSQL_DATABASE**. You can use default [mysql container](../#mysql)

exposed port **9000**

volume **/app/sonarqube/conf**, don't map at startup, use to backup only

volume **/app/sonarqube/logs**

volume **/app/sonarqube/extensions/plugins**

volume **/app/sonarqube/extensions/jdbc-driver**

default use for sonar is **admin**, password **admin**, you must change it.
