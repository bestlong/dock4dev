FROM phusion/baseimage:latest

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN DEBIAN_FRONTEND=noninteractive

RUN set -ex; apt-get update && apt-get install -y \
      language-pack-en-base \
      software-properties-common \
      git \
 && locale-gen en_US.UTF-8 \
 && add-apt-repository -y ppa:ondrej/php \
 && apt-get update \
 && apt-get install -y \     
     php7.2-cli \
     php7.2-curl \
     php7.2-intl \
     php7.2-gd \
     php7.2-gmp \
     php7.2-imap \
     php7.2-ldap \
     php7.2-mbstring \
     php7.2-mysql \
     php7.2-opcache \
     php7.2-pgsql \
     php7.2-phpdbg \
     php7.2-soap \
     php7.2-sqlite3 \
     php7.2-xml \
     php7.2-xsl \
     php7.2-zip \
     php7.2-dev \
     && curl -s https://getcomposer.org/installer | php \
     && mv composer.phar /usr/local/bin/composer \
 && cat /etc/os-release

# ENV LC_ALL="en_US.UTF-8"
ENV LANG="en_US.UTF-8" \
    LC_ALL="en_US.UTF-8"

# RUN apt-get update \
#  && apt-get install -y software-properties-common \
#  && add-apt-repository -y ppa:ondrej/php \
#  && apt-get update

# RUN apt-get update \
#  && apt-get install -y language-pack-en-base
# RUN apt-get install -y software-properties-common
# RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php

# RUN echo "export PATH=~/.bin:${PATH}" >> ~/.bashrc

     # && mkdir ~/.bin \
     # && mv composer.phar ~/.bin \

WORKDIR /var/www
