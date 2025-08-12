# 1st stage: Build the JAR
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy pom.xml and download dependencies first (for caching)
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy the rest of the project files
COPY src ./src

# Package the application
RUN mvn clean package -DskipTests

# 2nd stage: Run the JAR
FROM openjdk:21-jdk-slim

WORKDIR /app

# Copy only the built JAR from the previous stage
COPY --from=build /app/target/*.jar Hobbie.jar

# Expose the port your app runs on
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "Hobbie.jar"]
