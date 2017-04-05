#FROM php:fpm
FROM nginx:latest

MAINTAINER Brunekninja <bruno.drzanic@gmail.com>

# Install the PHP extensions we need
RUN apt-get update \
  && apt-get install -y \
    zip \
    git

# Workdir
#WORKDIR /var/www/wordpress

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer 
RUN composer create-project roots/bedrock wordpress