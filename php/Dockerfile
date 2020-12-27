FROM php:8.0-fpm
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        apt-utils \
        zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# Timezone
ARG TZ
RUN apt-get install -y tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    echo ${TZ} > /etc/timezone

# Composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

# coofiguration
COPY php.ini /usr/local/etc/php/

