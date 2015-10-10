FROM php:5.6-fpm
# Install modules
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo pdo_mysql mbstring

RUN apt-get install -y build-essential
RUN apt-get install -y curl
RUN pecl install intl
RUN apt-get update
RUN apt-get install -y git

#Install nodejs

RUN curl --silent --location https://deb.nodesource.com/setup_4.x | bash -
RUN apt-get install -y nodejs
RUN npm install -g bower --allow-root
RUN npm install -g less --allow-root
RUN npm install -g uglifyjs --allow-root

#Install Java
RUN apt-get install -y openjdk-7-jdk

RUN usermod -u 1000 www-data

CMD ["php-fpm"]
