FROM php:7.2.34-apache-buster

RUN apt-get update && \
    apt-get install -y locales && \
    locale-gen ja_JP.UTF-8 && \
    rm -rf /var/lib/apt/lists/*
ENV TZ Asia/Tokyo \
    LANG ja_JP.UTF-8 \
    LANGUAGE ja_JP:ja \
    LC_ALL=ja_JP.UTF-8 \
    COMPOSER_ALLOW_SUPERUSER=1 \
    COMPOSER_HOME=/composer

RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8DX

RUN pecl install xdebug-2.9.8 && \
    docker-php-ext-enable xdebug && \
    docker-php-ext-install pdo_mysql

# composer command
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer