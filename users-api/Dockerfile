# Use Maven as the base image for building the application
FROM maven:3.3-jdk-8 AS build

# Set working directory
WORKDIR /app

# Copy the Maven project files
COPY pom.xml .
COPY src ./src

# Build the application (equivalent to ./mvnw clean install)
RUN mvn clean install -DskipTests

# Use a smaller base image for the final runtime
FROM openjdk:8-jre-alpine

# Set working directory
WORKDIR /app

# Copy the built JAR file from the build stage
COPY --from=build /app/target/users-api-0.0.1-SNAPSHOT.jar app.jar

# Expose the required port
EXPOSE 8083

# Start the application
CMD ["java", "-jar", "app.jar"]