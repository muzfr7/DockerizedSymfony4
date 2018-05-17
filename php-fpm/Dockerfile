FROM php:7.2-fpm

MAINTAINER "Muzafar Jatoi <muzfr7@gmail.com>"

RUN apt-get update

### MYSQL DEPENDENCIES MUST BE ADDED ###

RUN apt-get update && apt-get install -y zlib1g-dev libpq-dev git libicu-dev libxml2-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install pdo pdo_mysql mysqli \
    && docker-php-ext-install zip xml

RUN curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Berlin /etc/localtime
RUN "date"

COPY php.ini /usr/local/etc/php/

WORKDIR /var/www