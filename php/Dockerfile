FROM php:7.4.8-apache
RUN apt-get update && apt-get -y upgrade && apt-get install -y git zlib1g-dev libzip-dev
RUN docker-php-ext-install pdo pdo_mysql mysqli
RUN a2enmod rewrite
# Install Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php composer-setup.php --install-dir=. --filename=composer && mv composer /usr/local/bin/
# Install Redis
RUN pecl install -o -f redis && rm -rf /tmp/pear && docker-php-ext-enable redis
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
EXPOSE 80
