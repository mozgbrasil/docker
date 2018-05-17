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

    mkdir -p ~/dados/dockers

    git clone https://github.com/mozgbrasil/docker mozg-docker

    docker-compose up

    # OR

    docker-compose --file docker-compose-bitnami.yml up --build

## **Web server:**

http://localhost:87
http://localhost:87/phpinfo.php

http://localhost:88
http://localhost:88/phpinfo.php

## **PHPMyAdmin:** 

http://localhost:8087
http://localhost:8088

## **Local emails:** 

http://localhost:8025

## Perguntas mais frequentes "FAQ"
<!--
#### Util

    -

    docker images && docker images ps && docker ps

    -

    docker-compose down --remove-orphans

    docker-compose up --build

    docker-compose exec --user root bitnami-apache bash

    -

    docker-compose --file docker-compose-bitnami.yml down --remove-orphans

    docker-compose --file docker-compose-bitnami.yml up --build

    docker-compose --file docker-compose-bitnami.yml exec --user root bitnami-apache bash

    docker-compose --file docker-compose-bitnami.yml exec --user root bitnami-fix-php-fpm bash

    docker-compose restart bitnami-php-fpm

    docker-compose restart bitnami-apache

    -








    
    docker network ls && docker network prune && docker service ls

    docker-compose exec php bash

    docker run -it --name phpfpm -v ./app:/app bitnami/php-fpm

    mkdir apache-vhost

    docker rmi -f ebfbbf98d46f

    docker-compose down --remove-orphans

    docker run -it bash

    docker-compose exec --user root mariadb bash
    

#### Build-Start | Re-Build

    cd ~/dados/git/projects/docker

    docker-compose up

    ./start



    docker-compose up -d --build # Re-Build

    docker-compose up --build # Re-Build

#### FIX: privileges image
#### FIX: var/www/.composer/cache/vcs does not exist and could not be created

    cd ~/dados/git/projects/docker

    docker-compose exec --user root apache chown www-data:www-data /var/www/.npm -Rf

    docker-compose exec --user root apache chown www-data:www-data /var/www/.composer -Rf
-->

## Contribuintes

Equipe Mozg

## License

[Comercial License](LICENSE.txt)

:cat2:
