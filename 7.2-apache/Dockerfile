FROM php:7.2-apache

RUN apt-get update && \
    apt-get install --yes --no-install-recommends \
        libmagickwand-dev libmagickwand-6.q16-3 libmagickwand-6.q16hdri-3 \
        libmemcached-dev libmemcached11 libmemcachedutil2 \
        postgresql-server-dev-9.6 libpq5 \
        git cron && \
    pecl install memcached && \
    docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql bcmath && \
    docker-php-ext-enable memcached && \
    apt-get remove --yes libmagickwand-dev libmemcached-dev postgresql-server-dev-9.6 && \
    apt-get autoremove --yes && \
    rm -rf /var/lib/apt/lists/* && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
