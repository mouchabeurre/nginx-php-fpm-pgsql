FROM php:7.2.3-fpm-stretch

RUN apt-get update
RUN apt-get install -y libpq-dev
RUN docker-php-ext-install pgsql pdo_pgsql
RUN docker-php-ext-enable pdo_pgsql

WORKDIR "/var/www/html"
