# Step 1: Use a Maven base image to build the project
FROM maven:3.8.1-openjdk-11 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy all files into the container
COPY . .

# Build the application using Maven
RUN mvn clean install

# Step 2: Create the final image to run the application
FROM openjdk:11-jre-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the previous step
COPY --from=build /app/email-writer-sb/target/email-writer-sb-0.0.1-SNAPSHOT.jar /app/

# Expose the port that your app will run on
EXPOSE 8080

# Command to run your application
CMD ["java", "-jar", "email-writer-sb-0.0.1-SNAPSHOT.jar"]
