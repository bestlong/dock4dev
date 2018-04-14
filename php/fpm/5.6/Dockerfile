FROM php:5.6-fpm

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
        libmcrypt-dev \
    && docker-php-ext-install mcrypt mysqli pdo_mysql \
    && php -m

WORKDIR /var/www
