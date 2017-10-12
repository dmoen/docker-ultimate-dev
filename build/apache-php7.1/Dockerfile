FROM php:7.1.10-apache

COPY php.ini /usr/local/etc/php/conf.d

COPY apache-hosts /etc/apache2/

RUN apt-get update -y && apt-get -y upgrade && apt-get -y install php-pear

RUN pear config-set php_ini /usr/local/etc/php/php.ini \
	&& pecl config-set php_ini /usr/local/etc/php/php.ini

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini