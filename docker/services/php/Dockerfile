FROM php:7.3.9-fpm-alpine

LABEL maintainer="Dark Jinnee <darkjinnee@gmail.com>"

RUN apk update && apk upgrade && apk add --no-cache \
    git \
	bash \
	curl \
	gettext \
	supervisor\
	libxml2-dev \
	freetype-dev \
	libpng-dev \
	libjpeg-turbo-dev \
	curl-dev \
	libzip-dev \
	&& docker-php-ext-install -j$(nproc) \
	ctype \
	json \
	mbstring \
	pdo \
	pdo_mysql \
	tokenizer \
	xml \
	iconv \
	curl \
	zip \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd \
	&& curl -sS https://getcomposer.org/installer -o composer-setup.php \
	&& php composer-setup.php --install-dir=/usr/local/bin --filename=composer

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-2.7.0 \
    && docker-php-ext-enable xdebug

RUN addgroup -g 1000 dev \
    && adduser -u 1000 -G dev -s /bin/sh -D dev
