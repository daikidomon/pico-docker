FROM php:8.0-fpm
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
         apt-utils \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

ARG TZ
RUN apt-get install -y tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    echo ${TZ} > /etc/timezone
#    apk add --update --no-cache \
#      icu-dev=~64.2 \
#      libzip-dev=~1.5 \
#      oniguruma-dev=~6.9

#RUN curl -sSL https://getcomposer.org/installer | php && \
#    php composer.phar create-project picocms/pico-composer pico

COPY php.ini /usr/local/etc/php/


#dom mbstring