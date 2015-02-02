Supported tags and respective Dockerfile links

* [1.580.2, latest](1.580.2/Dockerfile)


# Jenkins
http://jenkins-ci.org/

https://registry.hub.docker.com/_/jenkins/

# Build

`docker build --tag=pmpinson/jenkins:1.580.2 .`

`docker build --tag=pmpinson/jenkins .`

# Usage

`docker run -d -p pmpinson/jenkins`

must provide :
* -v /var/run/docker.sock:/var/run/docker.sock : if you want to use docker in jenkins build

exposed port **8080** and **50000** (for slave agent)

volume **/var/jenkins_home**
