FROM php:5.6-fpm

ENV TZ=Asia/Taipei

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
        libmcrypt-dev \
    && docker-php-ext-install mcrypt mysqli pdo_mysql \
    && php -m

WORKDIR /var/www
