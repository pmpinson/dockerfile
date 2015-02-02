FROM dockerfile/java:oracle-java8
MAINTAINER Pierre-Marie Pinson, pmpinson@gmail.com

RUN apt-get update && apt-get upgrade -y && \
	wget http://dist.sonar.codehaus.org/sonarqube-5.0.zip && \
	unzip sonarqube-5.0.zip -d /app && \
	rm -f sonarqube-5.0.zip

RUN sed -i 's|#sonar.web.javaAdditionalOpts=|sonar.web.javaAdditionalOpts=-server|g' /app/sonarqube-5.0/conf/sonar.properties && \
	sed -i 's|#sonar.jdbc.username=sonar|sonar.jdbc.username=root|g' /app/sonarqube-5.0/conf/sonar.properties && \
	sed -i 's|#sonar.jdbc.password=sonar|sonar.jdbc.password=${env:DB_ENV_MYSQL_ROOT_PASSWORD}|g' /app/sonarqube-5.0/conf/sonar.properties && \
	sed -i 's|#sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar|sonar.jdbc.url=jdbc:mysql://db:${env:DB_PORT_3306_TCP_PORT}/${env:DB_ENV_MYSQL_DATABASE}|g' /app/sonarqube-5.0/conf/sonar.properties && \
	sed -i 's|wrapper.java.command=java|#wrapper.java.command=java|g' /app/sonarqube-5.0/conf/wrapper.conf && \
	sed -i 's|#wrapper.java.command=/path/to/my/jdk/bin/java|wrapper.java.command=/usr/lib/jvm/java-8-oracle/bin/java|g' /app/sonarqube-5.0/conf/wrapper.conf

#RUN ln -s /app/sonarqube-5.0/conf /app/conf && \
#	ln -s /app/sonarqube-5.0/logs /app/logs && \
#	ln -s /app/sonarqube-5.0/extensions/plugins /app/plugins && \
#	ln -s /app/sonarqube-5.0/extensions/jdbc-driver /app/jdbc-driver

EXPOSE 9000

VOLUME /app/conf

VOLUME /app/logs

VOLUME /app/plugins

VOLUME /app/jdbc-driver

CMD ["/app/sonarqube-5.0/bin/linux-x86-64/sonar.sh", "console"]
