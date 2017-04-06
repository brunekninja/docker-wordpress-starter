FROM php:fpm

MAINTAINER Brunekninja <bruno.drzanic@gmail.com>

# Install latest community nginx
RUN apt-get update && apt-get install -y nginx

# Install the PHP extensions we need
RUN apt-get update \
  && apt-get install -y \
    zip \
    git

# Configure nginx
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer 

# Copy start.sh into the container
RUN mkdir -p /etc/service/nginx
COPY start.sh /etc/service/nginx/start.sh
RUN chmod +x /etc/service/nginx/start.sh

# Workdir
WORKDIR /var/www/

RUN rm -rf /app

# Install bedrock
RUN composer create-project roots/bedrock app

# Expose HTTP port
EXPOSE 80

CMD ["/etc/service/nginx/start.sh"]

## Cleanup
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*