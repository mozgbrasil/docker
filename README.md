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

### Docker Cytopia Config

    cd ~/dados/containers_docker

    git clone https://github.com/cytopia/devilbox devilbox-2019-02-18

        CONFIG

            docker-compose.yml

                php & http

                    # Mount volumes related to ln -s htdocs
                    - /home/marcio/dados/:/home/marcio/dados/


            .env

                DOCKER_LOGS=1
                PHP_SERVER=7.0
                HTTPD_SERVER=apache-2.4
                HOST_PATH_HTTPD_DATADIR=/home/marcio/dados/mount/www
                HOST_PATH_MYSQL_DATADIR=/home/marcio/dados/mount/mysql
                PHP_MODULES_ENABLE=ioncube

## Containers

	# https://github.com/SemanticComputing/docker-varnish

	cd /home/marcio/dados/git/clone/docker-varnish-2019-01-28 && ./docker-run.sh

## Run Image

    cd /home/marcio/dados/containers_docker/devilbox-2019-02-18-php56 && docker-compose down --remove-orphans && docker-compose up

### Removendo images e containers

    # https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

    # https://gist.github.com/bastman/5b57ddb3c11942094f8d0a97d461b430#docker---how-to-cleanup-unused-resources

    docker --version && docker images && docker images -a && docker images ps && docker ps && docker ps -a && docker network ls

    docker rm $(docker ps -a -f status=exited -q)

    docker rmi $(docker images -a -q)

    docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')

    docker rmi -f 08ee98d21fe3

# HTTPS
# https://github.com/devilbox/cert-gen#create-certificate-authority

cd /home/marcio/dados/git/clone/devilbox-2019-01-19/ca

ca-gen -v -c DE -s Berlin -l Berlin -o Devilbox -u Devilbox -n magento-dev02.devilbox -e ca@devilbox.org devilbox-rootCA.key devilbox-rootCA.crt

cert-gen -v -c DE -s Berlin -l Berlin -o Devilbox -u Devilbox \
           -n magento-dev02.devilbox -e admin@project.loc \
           -a '*.magento-dev02.devilbox,*.www.magento-dev02.devilbox' \
           devilbox-rootCA.key \
           devilbox-rootCA.crt \
           magento-dev02.devilbox.key \
           magento-dev02.devilbox.csr \
           magento-dev02.devilbox.crt

2.

devilbox-custom.conf

    ssl_certificate           /ca/magento-dev02.devilbox.crt;
    ssl_certificate_key       /ca/magento-dev02.devilbox.key;
    ssl_protocols             TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_ciphers               HIGH:!aNULL:!MD5;


# Otimizando Devilbox Nginx

    cat > cfg/nginx-stable/nginx.conf <<- _EOF_
    #
    # Nginx (stable) configuration overwrites
    #
    # Make sure this file ends by `*.conf`, otherwise
    # the configuration is not sourced by nginx.
    #
    # The below settings are just examples.
    # Copy them, remove them or reset them.
    #

    ## Example configuration:

    #send_timeout 60;

    tcp_nopush      on;
    tcp_nodelay     on;

    upstream fastcgi_backend {
        # use tcp connection
        # server httpd:9000;
        server php:9000;
        # or socket
        # server   unix:/var/run/php/php7.0-fpm.sock;
    }
    server {
        listen 80;
        server_name mage.devilbox;
        set $MAGE_ROOT /shared/httpd/localhost/htdocs/magento/magento-2.3.0-dev03;
        set $MAGE_MODE developer;
        include /shared/httpd/localhost/htdocs/magento/magento-2.3.0-dev03/nginx.conf.sample;
    }
    _EOF_

    cat > cfg/php-ini-7.2/devilbox-php.ini <<- _EOF_
    ;
    ; PHP.ini configuration
    ;
    [PHP]

    ; https://support.plesk.com/hc/en-us/articles/360005848254-How-to-set-up-Magento-2-1-0-on-Plesk-with-Nginx-only-hosting-option-enabled

    memory_limit = 2G
    max_execution_time = 1800
    zlib.output_compression = On
    session.save_path = "/var/lib/php/session"

    ; vim: set ft=dosini:
    _EOF_

    # How to check if php-fpm is running

    php-fpm --test
    php-fpm

    ps aux | grep php-fpm

    netstat -lntp

# Nginx Optimization

<!--
-

docker-compose down --remove-orphans

docker-compose up --build

docker-compose exec --user root library-apache bash

docker-compose exec --user www-data library-apache bash

-

docker-compose --file docker-compose-bitnami.yml down --remove-orphans

docker-compose --file docker-compose-bitnami.yml up --build

docker-compose --file docker-compose-bitnami.yml exec --user root bitnami-apache bash

docker-compose --file docker-compose-bitnami.yml exec --user root bitnami-fix-php-fpm bash

docker-compose restart bitnami-php-fpm

docker-compose restart bitnami-apache

-

echo -e "\e[1;33m --( docker version )-- \e[0m" ;\
docker --version ;\
echo -e "\e[1;33m --( docker images )-- \e[0m" ;\
docker images ;\
echo -e "\e[1;33m --( docker images ps )-- \e[0m" ;\
docker images ps ;\
echo -e "\e[1;33m --( docker ps )-- \e[0m" ;\
docker ps ;\
echo -e "\e[1;33m --( docker network ls )-- \e[0m" ;\
docker network ls ;\
echo -e "\e[1;33m --( docker service ls )-- \e[0m" ;\
docker service ls

docker-compose down --remove-orphans

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
