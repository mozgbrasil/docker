[checkmark]: https://raw.githubusercontent.com/mozgbrasil/mozgbrasil.github.io/master/assets/images/logos/logo_32_32.png "MOZG"
![valid XHTML][checkmark]

# Mozg\Docker

## Sinopse

Apache 2.4 + PHP 7.0 + OPCache + MariaDB + N98 Magerun 2 + XDebug + Redis

### Requirements

**MacOS:**

Install [Docker](https://docs.docker.com/docker-for-mac/install/), [Docker-compose](https://docs.docker.com/compose/install/#install-compose) and [Docker-sync](https://github.com/EugenMayer/docker-sync/wiki/docker-sync-on-OSX).

**Windows:**

Install [Docker](https://docs.docker.com/docker-for-windows/install/), [Docker-compose](https://docs.docker.com/compose/install/#install-compose) and [Docker-sync](https://github.com/EugenMayer/docker-sync/wiki/docker-sync-on-Windows).

**Linux:**

Install [Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/) and [Docker-compose](https://docs.docker.com/compose/install/#install-compose).

## Perguntas mais frequentes "FAQ"

#### Util

    docker images && docker images ps && docker ps

    docker rmi -f ebfbbf98d46f

    docker-compose down --remove-orphans
<!--
#### Build-Start | Re-Build

    cd ~/dados/git/projects/docker    

    ./start

    docker-compose up -d --build # Re-Build

    docker-compose up --build # Re-Build

-->
#### FIX: privileges image
#### FIX: var/www/.composer/cache/vcs does not exist and could not be created

    cd ~/dados/git/projects/docker

    docker-compose exec --user root apache chown www-data:www-data /var/www/.npm -Rf

    docker-compose exec --user root apache chown www-data:www-data /var/www/.composer -Rf

#### Install Magento

    cd ~/dados/git/projects/docker

    ./shell
    
    ls
    mkdir magento
    cd magento
    install-magento
    exit

#### Install Magento2

    cd ~/dados/git/projects/docker-php

    ./shell

    ls
    mkdir magento2
    cd magento2
    install-magento2
    exit

### Plataforma Magento1

    cd ~/dados/public_html

### Plataforma Magento2



#### Pull & Install

    cd ~/dados/public_html

    curl -s https://raw.githubusercontent.com/clean-docker/Magento2/master/init | bash -s docker-magento2 clone

    cd docker-magento2
    ./shell
    rm index.php
    install-magento2

#### Execute

### Panels

Enjoy your new panels!

**Web server:** http://localhost/

**PHPMyAdmin:** http://localhost:8080

**Local emails:** http://localhost:8025

### Features commands

| Commands  | Description  | Options & Examples |
|---|---|---|
| `./init`  | If you didn't use the CURL setup command above, please use this command changing the name of the project.  | `./init MYMAGENTO2` |
| `./start`  | If you continuing not using the CURL you can start your container manually  | |
| `./stop`  | Stop your project containers  | |
| `./kill`  | Stops containers and removes containers, networks, volumes, and images created to the specific project  | |
| `./shell`  | Access your container  | `./shell root` | |
| `./magento`  | Use the power of the Magento CLI  | |
| `./n98`  | Use the Magerun commands as you want | |
| `./grunt-init`  | Prepare to use Grunt  | |
| `./grunt`  | Use Grunt specifically in your theme or completely, it'll do the deploy and the watcher.  | `./grunt luma` |
| `./xdebug`  |  Enable / Disable the XDebug | |
| `./composer`  |  Use Composer commands | `./composer update` |

## Contribuintes

Equipe Mozg

## License

[Comercial License](LICENSE.txt)

:cat2:
