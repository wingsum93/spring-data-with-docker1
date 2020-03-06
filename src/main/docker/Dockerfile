#FROM openjdk:8-jdk-alpine
#WORKDIR /opt/webbbb
#ADD target/TV-Backend-1.0-SNAPSHOT.jar app.jar
#EXPOSE 3333
#ENTRYPOINT ["java","-jar","app.jar"]

# Step : Test and package
FROM maven:3.5.3-jdk-8-alpine as target
WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline
CMD echo ls

COPY src/ src/
RUN mvn package

# Step : Package image
FROM openjdk:8-jre-alpine
WORKDIR /opt/
EXPOSE 3333
COPY --from=target /build/target/TV-Backend-1.0-SNAPSHOT.jar /app/my-app.jar
CMD exec java $JAVA_OPTS -jar /app/my-app.jar
