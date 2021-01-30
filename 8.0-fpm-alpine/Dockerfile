FROM php:8-fpm-alpine

RUN apk add build-base zlib-dev git zip postgresql-dev

# Install PHP extensions
RUN docker-php-ext-install pdo pdo_pgsql

# Install composer 2
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --2
