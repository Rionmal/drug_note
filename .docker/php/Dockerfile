FROM php:${PHP_VERSION}-fpm
ENV SERVER_NAME ${SERVER_NAME}

####
# composer
####
COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

####
# npm
####
COPY --from=node:10.22 /usr/local/bin /usr/local/bin
COPY --from=node:10.22 /usr/local/lib /usr/local/lib

####
# package
####
RUN apt-get update \
&& apt-get install -y \
   git \
   zip \
   unzip \
   && docker-php-ext-install mysqli pdo pdo_mysql intl gd mbstring fileinfo

####
# timezone
####
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

####
# working directory
####
WORKDIR /var/www/html
