# Where to start

## Install docker:
Short version (may not be the last version):
  Fedora/RedHat:

        $ sudo dnf install docker

## Run docker daemon:
  Fedora/RedHat:

        $ sudo systemctl start docker

Complete story:
[Install docker](https://docs.docker.com/engine/installation/)

## Run an interactive shell in a container:

  Short version:
        docker run -t -i \<container_ID\> /bin/bash

        docker run -t -i ubuntu /bin/bash

Links to the [official docker documentation](https://docs.docker.com/):

[Docker basics](https://docs.docker.com/engine/userguide/basics/)

