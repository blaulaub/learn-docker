FROM docker.io/library/maven:3-openjdk-17 AS build
COPY . .
RUN mvn verify

FROM docker.io/library/maven:3-openjdk-17
COPY --from=build target/java-hello-world-0.0.1-SNAPSHOT-jar-with-dependencies.jar .
CMD java -jar java-hello-world-0.0.1-SNAPSHOT-jar-with-dependencies.jar
