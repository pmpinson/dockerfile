FROM jenkins
MAINTAINER Pierre-Marie Pinson, pmpinson@gmail.com

USER root

RUN apt-get update && \
        apt-get install -y docker.io

ENTRYPOINT ["/usr/local/bin/jenkins.sh"]
