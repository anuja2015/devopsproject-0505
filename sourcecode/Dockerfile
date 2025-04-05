# Use a base image with Java (JDK 17)
FROM openjdk:17


# Add the jar file created by Maven into the container
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENV PORT 3010

# Expose the application's port (default Spring Boot port is 8080)
EXPOSE $PORT

# Run the Spring Boot application
ENTRYPOINT ["java","-jar","-Xmx1024M","-Dserver.port=${PORT}","app.jar"]

