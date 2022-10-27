FROM openjdk:17-jdk-slim

# Download packages
RUN apt-get update && apt-get install -y \
    wget

RUN mkdir /minestom
WORKDIR /minestom

COPY temp-deps/minestom-base.jar minestom.jar

COPY temp-deps/world world

# Download plugins
RUN mkdir /minestom/extensions
WORKDIR /minestom/extensions

COPY temp-deps/lobby.jar lobby.jar

# Go back to the base directory for our server
WORKDIR /minestom
CMD ["java", "-jar", "/minestom/minestom.jar"]