# FROM adoptopenjdk/openjdk11:x86_64-alpine-jdk-11.0.14.1_1-slim
# ARG JAR_FILE=target/*.jar
# COPY ${JAR_FILE} app.jar
# EXPOSE 8080
# ENTRYPOINT ["java","-jar","/app.jar"]


# #
# # Build stage
# #
# FROM maven:3.8.5-jdk-11-slim AS build
# COPY src /home/app/src
# COPY pom.xml /home/app
# RUN mvn -f /home/app/pom.xml clean package

# #
# # Package stage
# #
# FROM openjdk:11-jre-slim
# COPY --from=build /home/app/target/*.jar /usr/local/lib/app.jar
# EXPOSE 8080
# ENTRYPOINT ["java","-jar","/usr/local/lib/app.jar"]

FROM openjdk:16-alpine3.13

WORKDIR /app

COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline

COPY src ./src

CMD ["./mvnw", "spring-boot:run"]