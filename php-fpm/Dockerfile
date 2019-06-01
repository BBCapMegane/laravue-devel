FROM php:7.2-fpm-alpine

RUN apk add --update --no-cache --virtual .build_deps unzip bzip2-dev zlib-dev gmp-dev && \
    apk add freshclam libpng-dev gmp && \
    docker-php-ext-install mysqli pdo_mysql bz2 gd zip && \
    apk del .build_deps && \
    freshclam && \
    apk add php7-xdebug --repository http://dl-3.alpinelinux.org/alpine/edge/testing/

COPY xdebug-config.ini /usr/local/etc/php/conf.d/xdebug-config.ini

RUN set -x \
  && deluser www-data \
	&& addgroup -g 50 -S www-data \
	&& adduser -u 1000 -D -S -G www-data www-data \
  && docker-php-ext-install opcache \
  && docker-php-ext-enable opcache

RUN docker-php-ext-install bcmath

COPY ./laravel.ini /usr/local/etc/php/conf.d/
COPY ./laravel.conf /usr/local/etc/php-fpm.d/

WORKDIR /var/www

RUN mkdir /run/clamav && chmod 0777 /run/clamav

CMD ["php-fpm"]

EXPOSE 9000
