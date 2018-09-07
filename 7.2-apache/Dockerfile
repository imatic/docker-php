FROM php:7.2-apache

RUN apt-get update && \
    apt-get install --yes libmagickwand-dev postgresql-server-dev-9.6 git libmemcached-dev && \
    pecl install memcached && \
    docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql && \
    docker-php-ext-enable memcached && \
    rm -rf /var/lib/apt/lists/* && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
