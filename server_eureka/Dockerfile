# Stage 1: Build
FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY ./pom.xml ./
COPY ./src ./src
RUN mvn clean package -DskipTests

# Étape 2 : Création de l'image finale avec OpenJDK
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar eureka-server.jar
ENTRYPOINT ["java", "-jar", "/app/eureka-server.jar"]