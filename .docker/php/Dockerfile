FROM php:fpm

MAINTAINER Brunekninja <bruno.drzanic@gmail.com>
# Install the PHP extensions we need
RUN apt-get update \
  && apt-get install -y \
    bzip2 \
    git

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
