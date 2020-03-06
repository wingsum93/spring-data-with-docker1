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
## run app in another user for safe reason
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ENV abc=a
EXPOSE 3333
COPY --from=target /build/target/TV-Backend-1.0-SNAPSHOT.jar /app/my-app.jar
ENTRYPOINT ["java","-jar","/app/my-app.jar"]
