# You can change this base image to anything else
# But make sure to use the correct version of Java
#FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
#ARG artifact=target/spring-boot-web.jar

#WORKDIR /opt/app

#COPY ${artifact} app.jar

# This should not be changed
#ENTRYPOINT ["java","-jar","app.jar"]
#--------------------------------------------------gcp------------
# Use a slim JDK base with compatibility for Cloud Run
FROM eclipse-temurin:17-jre-alpine

# Define artifact via build arg
ARG artifact=target/spring-boot-web.jar

# App directory
WORKDIR /app

# Copy jar into container
COPY ${artifact} app.jar

# Optional: Enable health check (optional but great for prod readiness)
HEALTHCHECK --interval=30s --timeout=5s CMD wget --spider http://localhost:8080/actuator/health || exit 1

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]

