FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    libpq-dev unzip\
    wget \
    zlib1g-dev \
    libfreetype6-dev \
    libmcrypt-dev \
    libjpeg62-turbo-dev \
    libzip-dev \
    libpng-dev \
    libicu-dev \
    libxml2-dev \
    libxslt-dev \
    zip

RUN apt-get update && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install soap \
    && docker-php-ext-install xsl \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install sockets

RUN apt-get update && apt-get install -y \
    libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
	&& docker-php-ext-enable imagick

RUN cd /usr/local/etc/php/conf.d/ && \
  echo 'memory_limit = -1' >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini

WORKDIR /app
