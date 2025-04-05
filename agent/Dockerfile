# Start with Maven image with JDK 17
FROM openjdk:17-slim

#Set env variables for Maven version
ENV MAVEN_VERSION=3.8.8
ENV MAVEN_HOME=/opt/maven
ENV PATH=$MAVEN_HOME/bin:$PATH

# Install Ansible
RUN  apt update && apt upgrade -y && apt install -y python3  \
    && apt install -y ansible
     

# Install Docker CLI and Maven
RUN apt update && apt install -y \
    docker.io \
    curl \
    git \
    && curl -fsSL https://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar -xz -C /opt && \
    ln -s /opt/apache-maven-$MAVEN_VERSION /opt/maven \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /app

# Ensure Maven and Docker are available
RUN mvn -version && docker --version \
    && ansible --version

# Default command (can be overridden)
CMD ["bash"]

