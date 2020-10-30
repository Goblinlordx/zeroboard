FROM php:7.4-apache

RUN apt-get update \
  && apt-get install -y libzip-dev libpng-dev \
  && docker-php-ext-install mysqli pdo_mysql zip gd \
  && a2enmod rewrite

RUN curl -L https://github.com/xpressengine/xe-core/releases/download/1.11.6/xe.1.11.6.tar.gz -o /tmp/xe.tar.gz \
  && rm -rf /var/www/html \
  && mkdir /tmp/xe \
  && tar -C /tmp/xe -zxvf /tmp/xe.tar.gz \
  && chown -R root:root /tmp/xe \
  && chmod -R 707 /tmp/xe \
  && mv /tmp/xe /var/www/html
