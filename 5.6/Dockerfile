# from https://www.drupal.org/requirements/php#drupalversions
FROM php:5.6-fpm

# install the PHP extensions we need
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libpq-dev \
	&& rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql zip opcache bcmath

# install phpredis extension
ENV PHPREDIS_VERSION 2.2.7

RUN curl -L -o /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz \
    && tar xfz /tmp/redis.tar.gz \
    && rm -r /tmp/redis.tar.gz \
    && mv phpredis-$PHPREDIS_VERSION /usr/src/php/ext/redis \
    && docker-php-ext-install redis

# install twig extension
ENV PHPTWIG_VERSION 1.21.1

RUN curl -L -o /tmp/twig.tar.gz https://github.com/twigphp/Twig/archive/v$PHPTWIG_VERSION.tar.gz \
    && tar xfz /tmp/twig.tar.gz \
    && rm -r /tmp/twig.tar.gz \
    && mv Twig-$PHPTWIG_VERSION /usr/src/php/ext/twig \
    && docker-php-ext-install twig

COPY config/php.ini /usr/local/etc/php/
