FROM php:7.4-fpm

RUN apt-get update
RUN apt-get install -y \
            git \
            libzip-dev \
            libc-client-dev \
            libkrb5-dev \
            libpng-dev \
            libjpeg-dev \
            libwebp-dev \
            libfreetype6-dev \
            libkrb5-dev \
            libicu-dev \
            zlib1g-dev \
            zip \
            ffmpeg \
            libmemcached11 \
            libmemcachedutil2 \
            build-essential \
            libmemcached-dev \
            gnupg2 \
            libpq-dev \
            libpq5 \
            libz-dev


RUN docker-php-ext-configure gd \
    --with-webp=/usr/include/ \
    --with-freetype=/usr/include/ \
    --with-jpeg=/usr/include/
RUN docker-php-ext-install gd

RUN docker-php-ext-configure imap \
    --with-kerberos \
    --with-imap-ssl
RUN docker-php-ext-install imap

RUN apt install -y libxml2-dev 

RUN docker-php-ext-configure zip

RUN docker-php-ext-install zip

RUN docker-php-ext-install dom

RUN docker-php-ext-install ctype

RUN docker-php-ext-install xml

RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install exif

RUN pecl install xdebug

RUN curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN pecl install memcached

RUN echo extension=memcached.so >> /usr/local/etc/php/conf.d/memcached.ini

ENV COMPOSER_ALLOW_SUPERUSER 1

WORKDIR /app
