# Use an official OpenJDK runtime as a parent image
FROM openjdk:21-jre-slim

# Set the working directory in the container
WORKDIR /app

# Copy the jar file into the container
COPY target/SimpleJavaApp-1.0-SNAPSHOT.jar /app/app.jar

# Run the jar file
CMD ["java", "-jar", "/app/app.jar"]
