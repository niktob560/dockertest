FROM php:fpm

RUN apt-get update && apt-get install -y \
curl \
wget \
git \
libfreetype6-dev \
libjpeg62-turbo-dev \
libxslt-dev \
libicu-dev \
libpng-dev \
libxml2-dev \
libzip-dev \
&& docker-php-ext-install -j$(nproc) iconv zip \
&& docker-php-ext-install -j$(nproc) gd


RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install xsl
RUN docker-php-ext-install soap

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www/test

CMD ["php-fpm"]
