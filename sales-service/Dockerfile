FROM openjdk:11.0.6-jdk-slim

ARG APP_DIR
ARG APP_JAR
ARG PRODUCTS_SERVICE_URL

# Adding a wait-for script for the MariaDB container
ENV WAIT_VERSION 2.7.3
ADD https://github.com/ufoscout/docker-compose-wait/releases/download/$WAIT_VERSION/wait /opt/wait
RUN chmod +x /opt/wait

WORKDIR /app
ADD ${APP_DIR}/${APP_JAR} /app
EXPOSE 8081

ENV APP_JAR=${APP_JAR}
ENV PRODUCTS_SERVICE_URL=${PRODUCTS_SERVICE_URL}
CMD /bin/bash -c "/opt/wait && java -jar $APP_JAR --products\-service.url=$PRODUCTS_SERVICE_URL \
  --spring.zipkin.base-url=http://zipkin:9411/"
