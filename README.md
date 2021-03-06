# Quick Start:
+ **Note**: This boilerplate is set in development enviroment
+ Clone
+ Start the container: `docker-compose up -d`

##### Enjoy!, services:
+ app
  + Alpine > Nginx + PHP FPM 7.4 (with xdebug) 
    - 8000:80, 8443:443, 10022:22
    - app.docker.test:80


+ mysql
  + MariaDB 10 (focal) 
    - 13306:3306
    - mysql:/var/lib/mysql


+ redis
  + Redis
    - redis:/data


+ mail
  + Mailhog
    - 8025:8025
    - mail.docker.test:8025 (it links the port 8025 to 80 | access without 8025)


+ phpmyadmin
  + PhpMyAdmin
    - phpmyadmin:/sessions
    - pma.docker.test:80


#### Additional, virtual host setup:
Run this docker image: https://hub.docker.com/r/nginxproxy/nginx-proxy  
Add these to your hosts file:
```
127.0.0.1      docker.test
127.0.0.1      pma.docker.test
127.0.0.1      app.docker.test
127.0.0.1      mail.docker.test
```
Restart your container: `docker-compose stop && docker-compose up -d`


#### To use XDebug, remember to set pathMappings, example for VSCode:
```
{
    "version": "0.2.0",
    "configurations": [{
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/app": "${workspaceRoot}/app",
            },
        },
    ]
}
```
`PHPStorm`: set path mappings here: `File -> Settings ->Languages and Frameworks -> PHP -> Servers`.
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


![PHP Docker Boilerplate](https://static.webdevops.io/php-docker-boilerplate.svg)

[![latest v5.2.0-beta3](https://img.shields.io/badge/latest-v5.2.0_beta3-green.svg?style=flat)](https://github.com/webdevops/php-docker-boilerplate/releases/tag/5.2.0-beta3)
![License MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)

This is an easy customizable docker boilerplate for any PHP-based projects like _Symfony Framework_, _CakePHP_, _Yii_ and many other frameworks or applications.

Supports:

- Nginx or Apache HTTPd
- PHP-FPM (with Xdebug)
- MySQL, MariaDB or PerconaDB
- PostgreSQL
- Solr (disabled, without configuration)
- Elasticsearch (disabled, without configuration)
- Redis (disabled)
- Memcached (disabled)
- Mailcatcher (if no mail sandbox is used, eg. [Vagrant Development VM](https://github.com/mblaschke/vagrant-development))
- FTP server (vsftpd)
- PhpMyAdmin
- maybe more later...

This Docker boilerplate is based on the [Docker best practices](https://docs.docker.com/articles/dockerfile_best-practices/) and doesn't use too much magic. Configuration of each docker container is available in the `docker/` directory - feel free to customize.

This boilerplate can also be used for any other web project. Just customize the makefile for your needs.

*Warning: There may be issues when using it in production.*

If you have any success stories please contact me.

You can use my [Vagrant Development VM](https://github.com/mblaschke/vagrant-development) for this Docker boilerplate, e.g. for easily creating new boilerplate installations with short shell command: `ct docker:create directory`.

## Table of contents

- [First steps / Installation and requirements](/documentation/INSTALL.md)
- [Updating docker boilerplate](/documentation/UPDATE.md)
- [Customizing](/documentation/CUSTOMIZE.md)
- [Services (Webserver, MySQL... Ports, Users, Passwords)](/documentation/SERVICES.md)
- [Docker Quickstart](/documentation/DOCKER-QUICKSTART.md)
- [Run your project](/documentation/DOCKER-STARTUP.md)
- [Container detail info](/documentation/DOCKER-INFO.md)
- [Troubleshooting](/documentation/TROUBLESHOOTING.md)
- [Changelog](/CHANGELOG.md)

## Credits

This Docker layout is based on https://github.com/denderello/symfony-docker-example/

Thanks for your support, ideas and issues.
- [Ingo Pfennigstorf](https://github.com/ipf)
- [Florian Tatzel](https://github.com/PanadeEdu)
- [Josef Florian Glatz](https://github.com/jousch)
- [Ingo M??ller](https://github.com/IngoMueller)
- [Benjamin Rau](https://twitter.com/benjamin_rau)
- [Philipp Kitzberger](https://github.com/Kitzberger)
- [Stephan Ferraro](https://github.com/ferraro)
- [Cedric Ziel](https://github.com/cedricziel)
- [Elmar Hinz](https://github.com/elmar-hinz)


Thanks to [cron IT GmbH](http://www.cron.eu/) for inspiration.

Did I forget anyone? Send me a tweet or create pull request!
