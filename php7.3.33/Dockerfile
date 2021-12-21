FROM php:7.3.33-fpm
RUN apt-get update && apt-get install -y --no-install-recommends \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libxpm-dev \
    libvpx-dev \
    libpng-dev \
    libmcrypt-dev \
    libicu-dev \
    libpq-dev \
    libzip-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd \
      --with-freetype-dir=/usr/include/ \
      --with-png-dir=/usr/include/ \
      --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install  -j "$(nproc)" gd \
    && docker-php-ext-install  intl \
    && docker-php-ext-install  zip \
    && docker-php-ext-install  pdo_mysql \
    && docker-php-ext-install  exif \
    && docker-php-ext-install  bcmath
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
