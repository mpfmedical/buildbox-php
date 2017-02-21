FROM php:5.6

RUN apt-get -qq update; \
	apt-get -qqy install git libmcrypt-dev zlib1g-dev; \
	docker-php-ext-install mcrypt zip mysql gd; \
	php -r "copy('https://getcomposer.org/installer', '/tmp/composer-setup.php');"; \
	php /tmp/composer-setup.php --install-dir=/bin --filename=composer; \
	rm -rf /var/lib/apt/lists/*