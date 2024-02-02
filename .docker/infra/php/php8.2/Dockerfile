FROM ubuntu:latest AS base

USER ${UID}:${GID}

ENV DEBIAN_FRONTEND noninteractive

# Install dependencies
RUN apt update
RUN apt install -y software-properties-common
RUN add-apt-repository -y ppa:ondrej/php
RUN apt update
RUN apt install -y php8.2\
    php8.2-cli\
    php8.2-common\
    php8.2-fpm\
    php8.2-mysql\
    php8.2-zip\
    php8.2-gd\
    php8.2-mbstring\
    php8.2-curl\
    php8.2-xml\
    php8.2-bcmath\
    php8.2-pdo

# Install php-fpm
RUN apt install -y php8.2-fpm php8.2-cli

# Install composer
RUN apt install -y curl
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY ./src /var/www/html
WORKDIR /var/www/html

RUN chown -R www-data:www-data /var/www/html

RUN mkdir -p /run/php

RUN sed -i 's|/run/php/php8.2-fpm.sock|9000|' /etc/php/8.2/fpm/pool.d/www.conf

ENTRYPOINT ["php-fpm8.2", "-F"]