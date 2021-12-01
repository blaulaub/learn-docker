FROM docker.io/library/debian
COPY etc_apt_sources.list /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y apt-file procps
RUN apt-file update
CMD /bin/bash