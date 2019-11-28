FROM php:7.3-fpm-alpine

# WORKDIR
ADD ./supervisord.conf /etc/supervisor/supervisord.conf
ADD php.ini /usr/local/etc/php/

RUN apk update && apk add --no-cache bash bash gzip curl unzip coreutils tzdata libjpeg-turbo-dev libpng-dev freetype-dev supervisor libzip-dev && \
    cp /usr/share/zoneinfo/Asia/Jakarta /etc/localtime && echo "Asia/Jakarta" > /etc/timezone && apk del tzdata && \
    docker-php-ext-configure zip --with-libzip && \
    docker-php-ext-install pdo pdo_mysql sockets zip pcntl && \
    docker-php-ext-configure gd \
        --with-gd \
        --with-freetype-dir=/usr/include/ \
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ && \
    NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    docker-php-ext-install -j${NPROC} gd &&\
    curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer && \
    rm -f /var/cache/apk/*

RUN php -v
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
