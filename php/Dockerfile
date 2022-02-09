FROM php:8.0-apache

RUN apt-get update && apt-get install vim libzip-dev libpng-dev libonig-dev zlib1g-dev g++ libicu-dev libpq-dev -y

RUN docker-php-ext-install mbstring zip gd pdo_mysql mysqli intl opcache

WORKDIR /var/www/laravel_docker

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN a2enmod rewrite