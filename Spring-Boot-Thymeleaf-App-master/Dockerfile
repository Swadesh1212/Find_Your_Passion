# 1st stage: Build the JAR
FROM maven:3.9.5-openjdk-21 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# 2nd stage: Run the JAR
FROM openjdk:21-jdk-slim
WORKDIR /app
COPY --from=build /app/target/Spring-Boot-Thymeleaf-App-master-0.0.1-SNAPSHOT.jar Hobbie.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "Hobbie.jar"]
