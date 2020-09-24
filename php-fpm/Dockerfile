FROM php:7.4-fpm-alpine3.12
RUN echo 'http://dl-4.alpinelinux.org/alpine/edge/community/' >> /etc/apk/repositories
ENV TIMEZONE=America/Santiago
ENV PHALCON_VERSION=4.0.5
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so 
RUN apk add tzdata && cp /usr/share/zoneinfo/America/Santiago /etc/localtime
RUN apk update && apk add --no-cache  \
    make \
    g++ \
    libzip \
    autoconf \
    file \
    libtool \
    libpng \
    libpng-dev \
    re2c \
    pcre-dev \
    gnu-libiconv \
    nano \
    php \
    php7-dev \
    php7-curl \
    php7-fpm \
    php7-gd \
    php7-intl \
    php7-json \
    php7-mbstring \
    php7-mcrypt \
    php7-memcached \
    php7-mysqli \
    php7-pdo \
    php7-pdo_mysql \
    php7-xdebug \
    php7-xml \
    php7-zip \
    php7-xsl \
    php7-redis \
    php7-opcache \
    php7-phar \
    php7-xmlwriter \
    php7-tokenizer \
    php7-simplexml \
    php7-ctype \
    php7-psr \
    tzdata \
    ca-certificates \
    git autoconf \
    file \
    g++ \
    gcc \
    libc-dev \
    make \
    pkgconf \
    re2c \
    libtool \
    check \
    check-dev \
    cyrus-sasl-dev \
    libsodium-dev \
    libssh2-dev \
    imagemagick-dev \
    yaml-dev \
    libzip \
    curl \
    libzip-dev
RUN set -xe && \
    curl -LO https://github.com/phalcon/cphalcon/archive/v${PHALCON_VERSION}.tar.gz && \
    tar xzf v${PHALCON_VERSION}.tar.gz && \
    # compile
    cd cphalcon-${PHALCON_VERSION}/build && ./install && \
    echo "extension=phalcon.so" > /usr/local/etc/php/conf.d/phalcon.ini && \
    cd ../.. && rm -rf v${PHALCON_VERSION}.tar.gz cphalcon-${PHALCON_VERSION}
RUN pecl install zlib zip
RUN cp /etc/php7/* /usr/local/etc/php/ -rf &&\
    mkdir /usr/local/etc/php/modulos/ && \
    cp /usr/lib/php7/modules/* /usr/local/etc/php/modulos/ && \
    cp /usr/local/lib/php/extensions/no-debug-non-zts-20190902/* /usr/local/etc/php/modulos/
RUN rm /usr/local/etc/php/conf.d/00_ctype.ini && \
    rm /usr/local/etc/php/conf.d/00_curl.ini && \
    rm /usr/local/etc/php/conf.d/00_dom.ini && \
    rm /usr/local/etc/php/conf.d/00_json.ini  && \
    rm /usr/local/etc/php/conf.d/00_mbstring.ini && \
    rm /usr/local/etc/php/conf.d/00_openssl.ini  && \
    rm /usr/local/etc/php/conf.d/00_pdo.ini  && \
    rm /usr/local/etc/php/conf.d/00_session.ini  && \
    rm /usr/local/etc/php/conf.d/00_simplexml.ini  && \
    rm /usr/local/etc/php/conf.d/00_tokenizer.ini  && \
    rm /usr/local/etc/php/conf.d/00_xml.ini  && \
    rm /usr/local/etc/php/conf.d/00_xmlwriter.ini  && \
    rm /usr/local/etc/php/conf.d/01_mysqlnd.ini && \
    rm /usr/local/etc/php/conf.d/01_phar.ini  
RUN mkdir 777 /sesion/ 
RUN apk add composer
