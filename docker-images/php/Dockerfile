FROM php:7.4-fpm-alpine

# PECL dependancies.
RUN apk add --no-cache \
    $PHPIZE_DEPS \
    openssl-dev

# Bash.
RUN apk add --no-cache bash

# Redis.
RUN pecl install redis && docker-php-ext-enable redis

# Lumen packages.
RUN docker-php-ext-install tokenizer mysqli pdo_mysql

# Xdebug configuration.
RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-2.9.5 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/xdebug.ini
