# About

This folder contains a `Dockerfile` creating a customized image based on docker.io debian (latest by default).

Customization concerns:
- using my local Debian repository
- pre-updating apt
- pre-installing some packages (not important)

And then simply start `/bin/bash` (for interactive use).

# Usage

Building:

```
sudo podman build . -t patchcode-bullseye
```

Running:

```
sudo podman run -it --cpus 2 --memory 2G patchcode-bullseye
```

*That's all folks*