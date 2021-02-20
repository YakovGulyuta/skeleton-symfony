FROM php:7.4-fpm


RUN apt-get update && apt-get install -y \
    curl \
    mc \
    libpng-dev \
    wget \
    zlib1g-dev \
    libmcrypt-dev \
    libzip-dev \
    && docker-php-ext-install pdo pdo_mysql zip


#ADD ./06_xdebug.ini /usr/local/etc/php/conf.d/


COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions

RUN wget https://getcomposer.org/installer -O - -q | php -- --install-dir=/bin --filename=composer --quiet
ENV COMPOSER_ALLOW_SUPERUSER 1

WORKDIR /var/www/symfony
