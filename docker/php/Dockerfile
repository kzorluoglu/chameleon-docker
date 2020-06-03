FROM php:7.2.5-fpm

RUN apt-get update && apt-get install -y \
            curl \
            wget \
            git \
            libfreetype6-dev \
            libjpeg62-turbo-dev \
            libmcrypt-dev \
            libpng-dev \
            libpq-dev \
            libzip-dev \
            libicu-dev \
      && pecl install xdebug mcrpyt-1.0.1 \
      && docker-php-ext-enable xdebug mcrypt \
      && docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip \
      && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
      && docker-php-ext-install -j$(nproc) gd

RUN curl -Ss https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini
WORKDIR /var/www
CMD ["php-fpm"]

