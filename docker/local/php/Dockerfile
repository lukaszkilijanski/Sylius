FROM php:8.2-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    libxpm-dev \
    libzip-dev \
    libicu-dev \
    unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-install gd pdo pdo_mysql opcache zip exif intl

# Copy custom php.ini
COPY ./docker/local/php/php.ini /usr/local/etc/php/php.ini

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Add NodeSource official PPA for Node.js 20
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash -

# Install Node.js and npm
RUN apt-get install -y nodejs

WORKDIR /var/www/html