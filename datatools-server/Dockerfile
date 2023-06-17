# syntax=docker/dockerfile:1
FROM maven:3.8.7-openjdk-18-slim

COPY . /datatools

# Build jar
WORKDIR /datatools
RUN mvn package -DskipTests
RUN cp target/dt*.jar /datatools/
RUN mv dt*.jar datatools-server.jar

RUN mkdir -p /var/datatools_gtfs/gtfsplus

EXPOSE 4000

RUN apt-get update && apt-get install -y --no-install-recommends mc

#CMD bash
# Launch server
# This relies on a configuration volume and aws volume being present. See `docker-compose.yml`, or the example below
# Try: docker run --publish 4000:4000 -v ~/config/:/config datatools-latest

# java -XX:MaxRAMPercentage=95 -jar datatools-server.jar /config/env.yml /config/server.yml
CMD ["java", "-XX:MaxRAMPercentage=95", "-jar", "datatools-server.jar", "/config/env.yml", "/config/server.yml"]
