FROM php:7.4-fpm-alpine

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
    pecl install imagick && \
    docker-php-ext-configure gd --with-jpeg && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql bcmath && \
    docker-php-ext-enable memcached imagick && \
    apk del imagemagick-dev libmemcached-dev postgresql-dev libzip-dev autoconf gcc alpine-sdk libpng-dev jpeg-dev icu-dev && \
    mkdir -p /usr/local/apache2/htdocs && ln -s /var/www/html/public/ /usr/local/apache2/htdocs/public && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
