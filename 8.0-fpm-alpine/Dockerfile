FROM php:8.0-fpm-alpine

RUN apk add --no-cache \
        icu-dev icu \
        ghostscript \
        libzip-dev libzip \
        imagemagick-dev imagemagick libpng-dev libpng jpeg-dev jpeg \
        libmemcached-dev libmemcached \
        postgresql-dev libpq \
        autoconf gcc alpine-sdk \
        git && \
    pecl install memcached && \
#    pecl install imagick && \ (https://github.com/Imagick/imagick/issues/358)
    docker-php-ext-configure gd --with-jpeg && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql bcmath && \
    docker-php-ext-enable memcached && \
#    docker-php-ext-enable imagick && \
    apk del imagemagick-dev libmemcached-dev postgresql-dev libzip-dev autoconf gcc alpine-sdk libpng-dev jpeg-dev icu-dev && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
