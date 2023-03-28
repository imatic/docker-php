FROM php:8.1-apache

RUN apt-get update && \
    apt-get install --yes --no-install-recommends \
        libzip-dev \
        zlib1g-dev libmemcached-dev libmemcached11 libmemcachedutil2 \
        git cron && \
    pecl install memcached && \
    docker-php-ext-configure opcache && \
    docker-php-ext-install zip exif pdo_mysql bcmath && \
    docker-php-ext-enable memcached opcache

# gd
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev && \
    docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ && \
    docker-php-ext-install gd

# intl
RUN apt-get install -y libicu-dev && \
    docker-php-ext-configure intl && \
    docker-php-ext-install intl

# postgresql
RUN apt-get install -y libpq-dev && \
    docker-php-ext-install pdo_pgsql

RUN apt-get autoremove --yes && apt-get clean -y && rm -rf /var/lib/apt/lists/*

RUN curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
