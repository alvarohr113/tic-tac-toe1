# Use an official Gradle image to build the application
FROM gradle:7.3.3-jdk11 AS build

# Set the working directory
WORKDIR /home/gradle/project

# Copy the project files into the container
COPY --chown=gradle:gradle . .

# Build the project
RUN gradle build

# Use an official OpenJDK runtime image
FROM openjdk:11-jre-slim

# Set the working directory
WORKDIR /app

# Copy the built jar file from the build stage
COPY --from=build /home/gradle/project/build/libs/*.jar app.jar

# Expose the application port
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "app.jar"]
