FROM php:7.1-fpm

# Install useful libraries
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libpq-dev \
    libz-dev \
    libssl-dev \
    libmcrypt-dev \
    libmemcached-dev \
    curl \ 
    zlib1g-dev \ 
    libicu-dev \ 
    g++

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql \
  && docker-php-ext-install mcrypt \
  && docker-php-ext-configure gd \
    --enable-gd-native-ttf \
    --with-jpeg-dir=/usr/lib \
    --with-freetype-dir=/usr/include/freetype2 \
  && docker-php-ext-install gd \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && pecl install -o -f redis \
  && rm -rf /tmp/pear \
  && docker-php-ext-enable redis \
  && docker-php-ext-install bcmath \
  && docker-php-ext-configure intl \
  && docker-php-ext-install intl

COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Install PHPUnit
RUN php -r "copy('https://phar.phpunit.de/phpunit-6.phar', 'phpunit');" \
    && chmod +x phpunit \
    && mv phpunit /usr/bin/phpunit

RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD ["php-fpm"]

EXPOSE 9000
