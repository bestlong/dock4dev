FROM php:7.3-fpm

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN set -xe; ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
        libmcrypt-dev \
        libjpeg-dev libpng-dev \
    && docker-php-ext-install mysqli pdo_mysql gd \
    && pecl install mcrypt-1.0.2 \
    && docker-php-ext-enable mcrypt \
    && php -m | grep -q 'mysqli' \
    && php -m | grep -q 'pdo_mysql' \
    && php -m | grep -q 'gd' \
    && php -m | grep -q 'mcrypt'

RUN set -xe; \
    # pdo_dblib
    apt-get update && apt-get install -y freetds-bin freetds-dev \
    && ln -s /usr/lib/x86_64-linux-gnu/libsybdb.a /usr/lib/ \
    && curl -L -o /tmp/PHP-7.3.tar.gz https://github.com/php/php-src/archive/PHP-7.3.tar.gz \
    && tar zxf /tmp/PHP-7.3.tar.gz -C /tmp \
    && cd /tmp/php-src-PHP-7.3/ext/pdo_dblib \
    && phpize \
    && ./configure \
    && make && make install \
    && docker-php-ext-enable pdo_dblib \
    && rm -rf /tmp/PHP-7.3.tar.gz \
    && rm -rf /tmp/php-src-PHP-7.3 \
    && php -m | grep -q 'pdo_dblib'

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && php -m | grep -q 'xdebug'

WORKDIR /var/www

# RUN apt-get install -y libpng12-dev libfreetype6-dev libjpeg62-turbo-de
# RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# RUN docker-php-ext-install jpeg

### php-fpm 效能調整
RUN sed -i 's/pm.max_children = 5/pm.max_children = 20/g' /usr/local/etc/php-fpm.d/www.conf \
 && sed -i 's/pm.min_spare_servers = 1/pm.min_spare_servers = 2/g' /usr/local/etc/php-fpm.d/www.conf \
 && sed -i 's/pm.max_spare_servers = 3/pm.max_spare_servers = 4/g' /usr/local/etc/php-fpm.d/www.conf
