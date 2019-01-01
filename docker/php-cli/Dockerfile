FROM php:7.1.0

RUN apt-get update -y && apt-get install -y git zlib1g-dev libicu-dev libmcrypt-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-configure mcrypt \
    && docker-php-ext-install intl mcrypt mysqli pdo_mysql \
    && pecl install xdebug \
    && pear channel-discover pear.horde.org

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

COPY docker/php-cli/php.ini /usr/local/etc/php/

RUN mkdir -p /app
WORKDIR /app

