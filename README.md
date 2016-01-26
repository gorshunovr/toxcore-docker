# toxcore-docker

This is a **Dockerfile** for building and running [Docker](https://www.docker.com) container with a latest version of Tox ([toxcore](https://github.com/irungentoo/toxcore/)) DHT bootstrap daemon.

Image is based on latest [Debian Docker](https://hub.docker.com/_/debian/) image. Total size should be around ~210MiB, but it could be minimized even more.
* image runs only **tox-bootstrapd** daemon by default
* ports exposed: 33445/tcp, 33445/udp, 8080/tcp, 8080/udp
* LAN discovery is disabled
* bootstrap nodes loaded by default: [bootstrapd-conf-ipv64.txt](https://tox.0x10k.com/bootstrapd-conf-ipv64.txt), change to more appropriate [list of nodes](https://tox.0x10k.com/bootstrapd-conf) depending on your available networking connectivity in ADD section

Launch image and check logs:

    docker run -d --name toxcore_bootstrapd account/toxcore
    docker logs toxcore_bootstrapd

Launch image and drop to Bash shell:

    docker run -t -i --name toxcore_bootstrapd /bin/bash

Alternatively you may change CMD section in Dockerfile. **tox-bootstrapd** could be started from within the shell with _'service tox-bootstrapd start'_.

Note that you most probably would need to open firewall ports for the container to work properly.
