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

Changes made upon the initial (early) solution:
- split to a multi-staged build
- with different base images for build and final

Possible solutions to explore further:
- smaller JRE image
- maybe with another stage to reduce the number of downloads from the central Maven repository

*That's all folks*