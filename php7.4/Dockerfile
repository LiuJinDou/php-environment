FROM php:7.4.28-fpm

LABEL version="1.0"
LABEL description="redis-manage docker image customized for php environment development"
LABEL maintainer="LiuJinDou <1975876584@qq.com>"

ENV TZ=Asia/Shanghai

# Install Extendsions
RUN apt-get update && apt-get install -y \
    --no-install-recommends  libmcrypt-dev libfreetype6-dev libonig-dev libzip-dev libpng-dev zlib1g-dev libjpeg-dev \
    && apt-get install -y librabbitmq-dev \
    && docker-php-ext-install mysqli pdo_mysql

# Install Extendsions(memcache、swoole、redis、amqp、mongodb、xlswrite)
RUN  pecl install memcache-4.0.5.2 \
    && pecl install swoole-4.7.1 \
	&& pecl install redis \
	&& pecl install amqp \
    && pecl install mongodb \
	&& pecl install xlswriter \
	&& docker-php-ext-enable mongodb memcache redis amqp swoole xlswriter

RUN curl -o /usr/bin/composer https://mirrors.aliyun.com/composer/composer.phar \
    && chmod +x /usr/bin/composer

ENV COMPOSER_HOME=/tmp/composer

