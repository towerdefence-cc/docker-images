FROM openjdk:17-jdk-slim

# Download packages
RUN apt-get update && apt-get install -y \
    wget

# We manually set the Velocity version to avoid bugs
ENV VELOCITY_JAR_URL "https://api.papermc.io/v2/projects/velocity/versions/3.1.2-SNAPSHOT/builds/184/downloads/velocity-3.1.2-SNAPSHOT-184.jar"
# Plugin URLs we download
#ENV PLUGIN_A = ""

RUN mkdir /velocity
WORKDIR /velocity

# Download the Velocity jar
RUN wget -O velocity.jar $VELOCITY_JAR_URL
COPY temp-deps/velocity.toml .

# Download plugins
RUN mkdir /velocity/plugins
WORKDIR /velocity/plugins

COPY temp-deps/velocity-agones-integration.jar agones-integration.jar
COPY temp-deps/velocity-lobby-selector.jar lobby-selector.jar
COPY temp-deps/velocity-player-tracker.jar player-tracker.jar

# Go back to the base directory for our server
WORKDIR /velocity
CMD ["java", "-jar", "/velocity/velocity.jar"]