FROM php:7.4-apache

RUN apt-get update \
  && apt-get install -y libzip-dev libpng-dev \
  && docker-php-ext-install mysqli pdo_mysql zip gd \
  && a2enmod rewrite ssl \
  && a2ensite default-ssl

RUN curl -L https://github.com/xpressengine/xe-core/releases/download/1.11.6/xe.1.11.6.tar.gz -o /tmp/xe.tar.gz \
  && rm -rf /var/www/html \
  && mkdir /tmp/xe \
  && tar -C /tmp/xe -zxvf /tmp/xe.tar.gz \
  && chown -R root:root /tmp/xe \
  && chmod -R 707 /tmp/xe \
  && mv /tmp/xe /var/www/html

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/ssl-cert-snakeoil.key -out /etc/ssl/certs/ssl-cert-snakeoil.pem -subj "/C=AT/ST=Vienna/L=Vienna/O=Security/OU=Development/CN=example.com"