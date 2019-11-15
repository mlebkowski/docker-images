FROM centos:7

RUN yum install -y \
    epel-release \
    http://rpms.famillecollet.com/enterprise/remi-release-7.rpm && \
    yum install -y \
    bash \
    which \
    git \
    nginx \
    ca-certificates \
    sqlite   

ARG PHP_VERSION=72
RUN yum --enablerepo=remi-php${PHP_VERSION} -y install \
    composer \
    php-bcmath \
    php-cli \
    php-fpm \
    php-intl \
    php-mbstring \
    php-mcrypt \
    php-mysqlnd \
    php-pdo \
    php-pecl-apcu \
    php-pecl-imagick \
    php-pecl-redis \
    php-pecl-zip \
    php-pecl-sqlite \
    php-xdebug \
    php-opcache

RUN curl -Ls https://downloads.wkhtmltopdf.org/0.12/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz | tar Jxf - -C /tmp && \
    mv /tmp/wkhtmltox/bin/wkhtmltopdf /usr/bin && \
    rm -f /etc/php-zts.d/15-xdebug.ini \
          /etc/php.d/15-xdebug.ini

COPY php.ini /etc/php.d/99-dev.ini
COPY xdebug /usr/local/bin/xdebug
COPY composer /usr/local/bin/composer

RUN chmod +x /usr/local/bin/xdebug /usr/local/bin/composer

