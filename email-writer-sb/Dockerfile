# Step 1: Use OpenJDK 17 base image
FROM openjdk:17 AS build

# Install Maven
RUN apt-get update && apt-get install -y maven

# Set the working directory inside the container
WORKDIR /app

# Copy all files into the container
COPY . .

# Build the application using Maven
RUN mvn clean install

# Step 2: Create the final image to run the application
FROM openjdk:17-jre-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the previous step
COPY --from=build /app/email-writer-sb/target/email-writer-sb-0.0.1-SNAPSHOT.jar /app/

# Expose the port that your app will run on
EXPOSE 8080

# Command to run your application
CMD ["java", "-jar", "email-writer-sb-0.0.1-SNAPSHOT.jar"]
