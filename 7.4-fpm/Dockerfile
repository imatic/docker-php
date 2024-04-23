FROM php:7.4-fpm

RUN apt-get update && apt-get install --yes lsb-release ca-certificates curl
RUN install -d /usr/share/postgresql-common/pgdg && curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
RUN echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list
RUN apt-get update && \
    apt-get install --yes --no-install-recommends \
        ghostscript \
        libzip-dev libzip4 \
        libmagickwand-dev libmagickwand-6.q16-6 libmagickwand-6.q16hdri-6 \
        libmemcached-dev libmemcached11 libmemcachedutil2 \
        postgresql-server-dev-11 libpq5 \
        git cron && \
    pecl install memcached && \
    pecl install imagick && \
    docker-php-ext-configure gd --with-jpeg && \
    docker-php-ext-install zip gd exif intl pdo_pgsql pdo_mysql bcmath && \
    docker-php-ext-enable memcached imagick && \
    apt-get remove --yes libmagickwand-dev libmemcached-dev postgresql-server-dev-11 libzip-dev && \
    apt-get autoremove --yes && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir -p /usr/local/apache2/htdocs && ln -s /var/www/html/public/ /usr/local/apache2/htdocs/public && \
    curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
