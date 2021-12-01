# About

This folder contains a `Dockerfile` creating a customized image based on some docker.io maven.
This folder also contains a Java Maven project, rooted in `pom.xml`.

Customization concerns:
- run Maven to compile the source into byte code and package into a JAR file

And then simply run that JAR file using `java`.

# Usage

Building:

```
sudo podman build . -t java-hello-world
```

Running:

```
sudo podman run -it --cpus 1 --memory 1G java-hello-world
```

# Issues

There are a number of severe issues with the current implementation:
- the initial build pulls several hundred megabytes of image layers (this is for `docker.io/library/maven:3-openjdk-17`); maybe there is a smaller SDK available
- on each build, plenty of jar files are downloaded from the central maven repository, consuming bandwidth and build time
- the final image still carries the sources and the JDK (java development kit), while the final JAR and the JRE (Java runtime environment) would suffice

Possible solutions to explore:
- staged build, using the sources and JDK only during build, but packaging only the final JAR into an JRE image
- with different images for JDK and JRE, seeking the best (here: size and build time, but in general: size and performance)
- maybe with another stage to reduce the number of downloads from the central Maven repository

*That's all folks*