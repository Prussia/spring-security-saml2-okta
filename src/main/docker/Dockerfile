FROM frolvlad/alpine-oraclejdk8:full

RUN apk add --no-cache openssl  curl \
    && rm -rf /var/cache/apk/*

ENV APP_HOME /var/app
ENV LOG ${APP_HOME}/logs

RUN mkdir -p "$APP_HOME"
RUN mkdir -p "${LOG}"
VOLUME ["/tmp","${APP_HOME}","${LOG}"]

WORKDIR /
ADD spring-security-saml2-okta-0.0.1-SNAPSHOT.jar app.jar
RUN sh -c 'touch /app.jar'

ENV JAVA_OPTS=""

 
 

USER root

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Dlogging.file=${LOG}/samlservice.log -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]