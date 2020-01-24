FROM php:7.3-fpm 
RUN apt update && apt upgrade -y 
RUN apt-get update && apt-get install -y \
        zip \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libxml2 libxml2-utils \
    libxml2-dev \
    bzip2  libbz2-dev \
    libcurl4 \
    libcurl4-openssl-dev \
    # libtidy \
    libtidy-dev \
    libzip4 \
    libzip-dev \
    libxslt1-dev \
    libmagickwand-dev \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev libxpm-dev \
    libfreetype6-dev

RUN docker-php-ext-configure gd \
    --with-gd \
    --with-webp-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir \
    --with-xpm-dir \
    --with-freetype-dir 
    # --enable-gd-native-ttf

# RUN pecl install imagick
# RUN pecl install imagick-beta
RUN pecl install imagick && docker-php-ext-enable imagick

RUN  CFLAGS="-I/usr/src/php" docker-php-ext-install \
        gd mysqli  bz2 opcache \
        pdo pdo_mysql shmop intl exif \
        # imagick \
        curl \
        simplexml soap sockets tidy tokenizer bcmath \
        xml xmlreader  xmlrpc xsl zip

RUN apt-get update && apt-get install -y vim curl wget tmux git && apt-get clean

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

