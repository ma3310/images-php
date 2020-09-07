# Docker Hub: ma3310/php:7.4-nginx-ubuntu-20.04
FROM ubuntu:20.04

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8

# https://askubuntu.com/questions/365911/why-the-services-do-not-start-at-installation
# RUN echo "exit 0" > /usr/sbin/policy-rc.d

# Add Official MySQL Repo
ADD https://repo.mysql.com/mysql-apt-config_0.8.15-1_all.deb /tmp/mysql-apt-config.deb

# Installed modules:
#   composer from Composer Official
#   drush from Github
#   lynx from Ubuntu Official
#   nginx and php from ondrej
RUN apt-get update && apt-get install -y software-properties-common apt-utils curl lynx lsb-release unzip wget zsh \
  && dpkg -i /tmp/mysql-apt-config.deb \
  && add-apt-repository ppa:ondrej/nginx && add-apt-repository ppa:ondrej/php && apt-get update && apt-get upgrade -y \
  && apt-get install -y nginx-extras \
  php7.4 php7.4-bcmath php7.4-cli php7.4-curl php7.4-enchant php7.4-fpm php7.4-gd php7.4-gmp php7.4-json php7.4-mbstring php7.4-mysql php7.4-opcache php7.4-pgsql php7.4-soap php7.4-xml php7.4-xmlrpc php7.4-zip \
  php-tokenizer php-pear php-redis php-xdebug \
  mysql-client \
  && apt-get clean && rm -rf /var/lib/apt/lists/* && rm -f /tmp/mysql-apt-config.deb \
  && phpdismod xdebug \
  && curl -sSL https://github.com/drush-ops/drush/releases/download/8.4.1/drush.phar -o /usr/local/bin/drush \
  && chmod +x /usr/local/bin/drush \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

EXPOSE 80 443

CMD service php7.4-fpm start && nginx -g "daemon off;"
