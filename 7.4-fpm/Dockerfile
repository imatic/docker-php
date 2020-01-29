FROM php:7.4-fpm

RUN apt-get update && \
    apt-get install --yes --no-install-recommends \
        libzip-dev libzip4 \
        libmagickwand-dev libmagickwand-6.q16-6 libmagickwand-6.q16hdri-6 \
        libmemcached-dev libmemcached11 libmemcachedutil2 \
        postgresql-server-dev-11 libpq5 \
        git cron && \
    pecl install memcached && \
    pecl install imagick && \
    pecl install apcu && \
    pecl install apcu_bc && \
    docker-php-ext-configure gd --with-jpeg && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql bcmath && \
    docker-php-ext-enable memcached imagick apcu && \
    echo 'extension=apc.so' >> /usr/local/etc/php/conf.d/docker-php-ext-apcu.ini && \
    apt-get remove --yes libmagickwand-dev libmemcached-dev postgresql-server-dev-11 libzip-dev && \
    apt-get autoremove --yes && \
    rm -rf /var/lib/apt/lists/* && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
