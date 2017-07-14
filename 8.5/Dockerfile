FROM artem236/rpi-openjdk:jre

ENV TOMCAT_VERSION 8.5.16

RUN wget --quiet http://apache.volia.net/tomcat/tomcat-8/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz -O /tmp/tomcat.tgz && \
	mkdir /opt && \
	tar xzvf /tmp/tomcat.tgz -C /opt && \
	mv /opt/apache-tomcat-${TOMCAT_VERSION} /opt/tomcat && \
	rm /tmp/tomcat.tgz && \
	rm -rf /opt/tomcat/webapps/examples && \
	rm -rf /opt/tomcat/webapps/docs 

ADD tomcat-users.xml /opt/tomcat/conf/

ENV CATALINA_HOME /opt/tomcat
ENV PATH $PATH:$CATALINA_HOME/bin

EXPOSE 8080
EXPOSE 8009
VOLUME "/opt/tomcat/webapps"
WORKDIR /opt/tomcat

CMD ["/opt/tomcat/bin/catalina.sh", "run"]