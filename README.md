# PHP Images

Normally when we start PHP image, we intend to provide PHP environment for an application, which usually involve several PHP extensions as well. Official PHP image provides special commands to accomplish it, which is different with traditional way. This repository uses old school approach to integrates PHP extension to meet different requirements. We also provides variants using PHP official image approach to setup environment, user could refer to.

Access related Docker images at https://hub.docker.com/r/ma3310/php.

## ma3310/php:7.4-nginx-ubuntu-20.04

This image provides PHP 7.4 environment with extensions, as well as most used PHP tools, like composer, drush, etc. It bases on Ubuntu 20.04, integrates Ubuntu style nginx and PHP repository (https://launchpad.net/~ondrej) to setup nginx and PHP environment with latest stable version. 

With default configuration, this image only listen 80 port to serve html site, static project folder could be mount to /var/www/html to check result. 

User could prepare PHP sites configuration, then mount resident folder to /etc/nginx/sites-enabled.

Below PHP settings is updated from original values:

| Package       | Value    | Comments                  |
|---------------|----------|---------------------------|
| memory_limit  | 384M     |                           |

### Usage
``` bash
# Start with shipped docker-compose.yml file.
docker-compose -f '7.4-nginx-ubuntu-20.04/docker-compose.yml' up -d
```

## Official PHP 7.4-cli

### Usage
``` bash
docker run --rm -it php:7.4 bash
```
