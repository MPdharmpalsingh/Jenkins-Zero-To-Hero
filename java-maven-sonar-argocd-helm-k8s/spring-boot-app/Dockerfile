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
FROM maven:3.9.6-eclipse-temurin-17

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl unzip python3 python3-distutils gnupg apt-transport-https \
    && ln -s /usr/bin/python3 /usr/bin/python

# Install Google Cloud CLI
ENV CLOUD_SDK_VERSION=465.0.0
RUN curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    tar -xf google-cloud-sdk-${CLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
    ./google-cloud-sdk/install.sh --quiet && \
    ln -s /google-cloud-sdk/bin/gcloud /usr/bin/gcloud

ENV PATH="/google-cloud-sdk/bin:${PATH}"


