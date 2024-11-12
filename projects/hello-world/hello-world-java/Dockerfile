# Stage 1: Build a JAR file using Maven
# Use a Maven image with JDK 8 to build the application
FROM maven:3.8.2-jdk-8-slim AS stage1   
# Set the working directory to /home/app in the container
WORKDIR /home/app                       
# Copy all files from the current directory on the host to /home/app in the container
COPY . /home/app/                       
# Run Maven to clean the workspace and package the application into a JAR file
RUN mvn -f /home/app/pom.xml clean package   


# Stage 2: Create a lightweight image for running the application
# Use a lightweight OpenJDK 8 image for the runtime environment
FROM openjdk:8-jdk-alpine               
# Expose port 5000 to allow external access to this port
EXPOSE 5000                             
# Copy the JAR file built in stage 1 to the current container
COPY --from=stage1 /home/app/target/hello-world-java.jar hello-world-java.jar   
# Set the command to run the JAR file with Java when the container starts
ENTRYPOINT ["sh", "-c", "java -jar /hello-world-java.jar"]  
