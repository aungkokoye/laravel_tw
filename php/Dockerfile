FROM php:8.1-apache

RUN apt-get update && apt-get install vim libzip-dev libpng-dev libonig-dev zlib1g-dev g++ libicu-dev libpq-dev -y

RUN docker-php-ext-install mbstring zip gd pdo_mysql mysqli intl opcache

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs


WORKDIR /var/www/laravel_docker

RUN cd /var/www/laravel_docker && npm install

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN a2enmod rewrite
