FROM openjdk:11.0.6-jdk-slim

ARG APP_DIR
ARG APP_JAR

# Adding a wait-for script for the MariaDB container
ENV WAIT_VERSION 2.7.3
ADD https://github.com/ufoscout/docker-compose-wait/releases/download/$WAIT_VERSION/wait /opt/wait
RUN chmod +x /opt/wait

WORKDIR /app
ADD ${APP_DIR}/${APP_JAR} /app
EXPOSE 8082

ENV APP_JAR=${APP_JAR}
CMD /bin/bash -c "/opt/wait && java -Dspring.zipkin.base-url=http://zipkin:9411/ -jar $APP_JAR"
