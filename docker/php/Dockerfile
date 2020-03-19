FROM php:7.4-fpm
COPY php.ini /usr/local/etc/php/

ENV TZ Asia/Tokyo

RUN apt-get update \
  && apt-get install -y libzip-dev mariadb-client cron vim libonig-dev \
  && docker-php-ext-install zip pdo_mysql \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug

#Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('SHA384', 'composer-setup.php') === trim(file_get_contents('https://composer.github.io/installer.sig'))) { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php --version=1.10.0 \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/sbin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www
