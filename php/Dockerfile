FROM php:7.4-apache

WORKDIR /var/www/html

#Different another project
RUN docker-php-ext-install mysqli

COPY nginx.conf /etc/nginx/conf.d

COPY . .

RUN chmod -R 777 /var/www/html/