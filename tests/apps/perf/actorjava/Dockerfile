# build stage build the jar with all our resources
FROM maven:3-openjdk-11@sha256:805f366910aea2a91ed263654d23df58bd239f218b2f9562ff51305be81fa215 as build

VOLUME /tmp
WORKDIR /build

COPY pom.xml .
RUN mvn dependency:go-offline

ADD src/ /build/src/
RUN mvn package

# package stage
FROM openjdk:11-jre-slim@sha256:93af7df2308c5141a751c4830e6b6c5717db102b3b31f012ea29d842dc4f2b02

ARG JAR_FILE
COPY --from=build /build/target/app.jar /opt/app.jar
WORKDIR /opt/

EXPOSE 3000
ENTRYPOINT java -jar app.jar --server.port=3000
