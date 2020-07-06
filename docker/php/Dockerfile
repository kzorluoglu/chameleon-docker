FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
      curl \
      libmemcached-dev \
      memcached \
      wget \
      git \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      libmcrypt-dev \
      libpng-dev \
      libpq-dev \
      libzip-dev \
      libicu-dev \
      libonig-dev \
      libtidy-dev \
      && docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip tidy \
      && docker-php-ext-configure gd --with-jpeg=/usr/include/ --with-freetype=/usr/include/ \
      && docker-php-ext-install -j$(nproc) gd

RUN curl -Ss https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# apache
RUN rm -rfv /etc/apache2/sites-enabled/*.conf
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
RUN ln -s /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-enabled/000-default.conf
CMD ["apachectl","-D","FOREGROUND"]
RUN a2enmod rewrite
RUN usermod -u 1000 www-data
RUN chown www-data:www-data /var/www/html/

# memcached
RUN pecl install memcached-3.1.5
RUN docker-php-ext-enable memcached

# install xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug
COPY php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html