FROM docker.io/library/maven:3-openjdk-17
COPY . .
RUN mvn verify
CMD java -jar target/java-hello-world-0.0.1-SNAPSHOT-jar-with-dependencies.jar
