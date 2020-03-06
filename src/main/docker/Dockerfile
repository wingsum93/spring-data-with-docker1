FROM openjdk:8-jdk-alpine
VOLUME /tmp
# WORKDIR /opt/android
ADD ../../../target/docker/TV-Backend-1.0-SNAPSHOT.jar app.jar
RUN bash -c 'touch /app.jar'
EXPOSE 80
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]