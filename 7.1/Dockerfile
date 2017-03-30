FROM php:7.1

ENV PHANTOMJS_VERSION=2.1.1

RUN apt-get -qq update; \
    apt-get -qqy install libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev zlib1g-dev curl unzip bzip2 fontconfig ssh rsync; \
    curl -L https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2 -o /tmp/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2; \
    tar xvjf /tmp/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2 -C /tmp; \
    mv /tmp/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64/bin/phantomjs /usr/bin/phantomjs; \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include --with-jpeg-dir=/usr/include; \
    docker-php-ext-install gd mcrypt bcmath mbstring pdo_mysql zip; \
    php -r "copy('https://getcomposer.org/installer', '/tmp/composer-setup.php');"; \
    php /tmp/composer-setup.php --install-dir=/bin --filename=composer; \
    mkdir -p /root/.ssh; \
    chmod 0700 /root/.ssh; \
    touch /root/.ssh/known_hosts; \
    chmod 0600 /root/.ssh/known_hosts; \
    rm -rf /var/lib/apt/lists/*; \
    rm -rf /tmp/*
