# 1st stage: Build the JAR
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the Maven project files into the container
COPY Find_Your_Passion/Spring-Boot-Thymeleaf-App-master/ .

# Build the application without running tests
RUN mvn clean package -DskipTests

# 2nd stage: Run the JAR
FROM openjdk:21-jdk-slim

WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/*.jar app.jar

# Expose port 8080
EXPOSE 8080

# Run the JAR
ENTRYPOINT ["java", "-jar", "app.jar"]
