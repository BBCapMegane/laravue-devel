FROM php:7.2-alpine
MAINTAINER Niikura Rtyota <ryota.niikura@nijibox.co.jp>

RUN apk add --update --no-cache --virtual .build_deps unzip bzip2-dev zlib-dev gmp-dev $PHPIZE_DEPS && \
    apk add freshclam libpng-dev gmp && \
    docker-php-ext-install mysqli pdo_mysql bz2 gd zip gmp && \
    pecl install xdebug && docker-php-ext-enable xdebug && \
    apk del .build_deps && \
    freshclam

RUN curl -sS https://getcomposer.org/installer | php; mv composer.phar /usr/local/bin/composer ; mkdir /var/dev

RUN curl -L -o /usr/bin/phpmd http://static.phpmd.org/php/latest/phpmd.phar && chmod +x /usr/bin/phpmd
# RUN mkdir /var/www

WORKDIR /var/www

CMD ["sh"]
