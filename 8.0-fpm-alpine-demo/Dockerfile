FROM php:8.0-fpm-alpine

RUN mkdir -p /usr/local/apache2/htdocs /var/www/html/public && ln -s /var/www/html/public/ /usr/local/apache2/htdocs/public && \
   printf "<?php\nphpinfo();\n" > /var/www/html/public/index.php
