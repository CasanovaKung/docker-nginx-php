FROM php:7.2.6-fpm
LABEL maintrainer="Jakkrapan Wongchan<casanovakung@windowslive.com>"

ARG TZ=Asia/Bangkok

RUN set -x \
  && apt-get update && apt-get install -y \
  zlib1g-dev \
  libicu-dev \
  g++ \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  && docker-php-ext-configure intl \
  && docker-php-ext-install intl \
  && docker-php-ext-configure zip \
  && docker-php-ext-install zip \
  && docker-php-ext-configure mysqli \
  && docker-php-ext-install mysqli \
  && docker-php-ext-configure pdo_mysql \
  && docker-php-ext-install pdo_mysql \
  && cd /tmp \
  && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('SHA384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && mv /tmp/composer.phar /usr/bin/composer \
  && php -r "unlink('composer-setup.php');" \
  && echo -n

# RUN printf '[PHP]\ndate.timezone = "Asia/Bangkok"\n' > /usr/local/etc/php/conf.d/tzone.ini
ADD ./zz-overrides.ini /usr/local/etc/php/conf.d/zz-overrides.ini
RUN usermod -u 1000 www-data

EXPOSE 9000
CMD ["php-fpm", "-F"]
