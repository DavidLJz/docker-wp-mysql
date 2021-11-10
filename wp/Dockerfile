# https://hub.docker.com/_/wordpress

ARG wp_version

FROM wordpress:${wp_version}

RUN apt update

RUN apt install locales nano unzip less libcurl4-gnutls-dev libicu-dev libmcrypt-dev libvpx-dev libjpeg-dev libpng-dev libxpm-dev zlib1g-dev libfreetype6-dev libxml2-dev libexpat1-dev libbz2-dev libgmp3-dev libldap2-dev unixodbc-dev libpq-dev libaspell-dev libsnmp-dev libpcre3-dev libtidy-dev libzip-dev -yqq

RUN sed -i -e 's/# es_ES.UTF-8 UTF-8/es_ES.UTF-8 UTF-8/' /etc/locale.gen && \
	locale-gen 'es_ES.UTF-8' && \
	dpkg-reconfigure --frontend=noninteractive locales

RUN docker-php-ext-install mysqli pdo pdo_mysql mbstring curl json intl gd xml zip bz2 opcache

RUN a2enmod rewrite

COPY conf.d/* /usr/local/etc/php/conf.d/
COPY bin/* /usr/bin/