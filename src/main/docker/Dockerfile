FROM openjdk:8-jdk-alpine
WORKDIR /opt/webbbb
ADD target/TV-Backend-1.0-SNAPSHOT.jar app.jar
EXPOSE 3333
ENTRYPOINT ["java","-jar","app.jar"]