FROM php:5.6

RUN apt-get -qq update; \
    apt-get -qqy install libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev zlib1g-dev curl unzip; \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include --with-jpeg-dir=/usr/include; \
    docker-php-ext-install gd mcrypt bcmath mbstring pdo_mysql; \
    php -r "copy('https://getcomposer.org/installer', '/tmp/composer-setup.php');"; \
    php /tmp/composer-setup.php --install-dir=/bin --filename=composer; \
    rm -rf /var/lib/apt/lists/*
