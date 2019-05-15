[checkmark]: https://raw.githubusercontent.com/mozgbrasil/mozgbrasil.github.io/master/assets/images/logos/logo_32_32.png "MOZG"
![valid XHTML][checkmark]

# Mozg\Docker

## Sinopse

Baseado em

https://docs.bitnami.com/containers/how-to/create-amp-environment-containers/

### Requirements

**MacOS:**

Install [Docker](https://docs.docker.com/docker-for-mac/install/), [Docker-compose](https://docs.docker.com/compose/install/#install-compose) and [Docker-sync](https://github.com/EugenMayer/docker-sync/wiki/docker-sync-on-OSX).

**Windows:**

Install [Docker](https://docs.docker.com/docker-for-windows/install/), [Docker-compose](https://docs.docker.com/compose/install/#install-compose) and [Docker-sync](https://github.com/EugenMayer/docker-sync/wiki/docker-sync-on-Windows).

**Linux:**

Install [Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/) and [Docker-compose](https://docs.docker.com/compose/install/#install-compose).

## Pull & Run

    cd ~/dados/git/clone

    git clone https://github.com/mozgbrasil/docker mozg_docker

    cd mozg_docker

    docker-compose up

    # OR

    docker-compose --file docker-compose-bitnami.yml up --build

## **Web server:**

http://localhost

http://localhost/phpinfo.php

## **PHPMyAdmin:**

http://localhost:8080

user: root

## **Local emails:**

http://localhost:8025

## Perguntas mais frequentes "FAQ"

## Contribuintes

Equipe Mozg

## License

[Comercial License](LICENSE.txt)

:cat2:
