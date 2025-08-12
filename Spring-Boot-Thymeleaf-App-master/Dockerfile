# Use Eclipse Temurin JDK 21 base image (Ubuntu Jammy)
FROM eclipse-temurin:21-jdk-jammy

# Set working directory inside the container
WORKDIR /app

# Copy the built jar file into the container
COPY target/hobbie-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 (adjust if your app runs on a different port)
EXPOSE 8080

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "app.jar"]
