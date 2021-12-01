# About

This folder contains a `Dockerfile` creating a customized image based on docker.io node (latest 'alpine' by default).

Customization concerns:
- copy some javascript code file into the container

And then simply run that javascript code file.

# Usage

Building:

```
sudo podman build . -t node-js-hello-world
```

Running:

```
sudo podman run --cpus 1 --memory 2G node-js-hello-world
```

*That's all folks*