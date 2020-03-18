FROM php:7.4-fpm

# Update packages
RUN apt-get update

#####################################
# Curl
#####################################
# Install curl and requirements
RUN apt-get install -y --no-install-recommends libcurl4-openssl-dev \
    && docker-php-ext-install curl

#####################################
# GIT
#####################################
# Install git
RUN apt-get install -y --no-install-recommends git

#####################################
# Compression
#####################################
# Install zip, bz2 and requirements
RUN apt-get install -y --no-install-recommends zip unzip libzip-dev libbz2-dev zlib1g-dev \
    && docker-php-ext-install zip \
    bz2 

#####################################
# MCrypt:
#####################################
# Install mcrypt and requirements
RUN apt-get install -y --no-install-recommends libmcrypt-dev \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt

#####################################
# MySQL PDO
#####################################
# Install mysql pdo
RUN docker-php-ext-install pdo_mysql

#####################################
# GD
#####################################
# Install gd and requirements
RUN apt-get install -y --no-install-recommends libjpeg-dev libpng-dev libfreetype6-dev \
    && docker-php-ext-configure gd \
    --with-jpeg \
    --with-freetype \
    && docker-php-ext-install gd

#####################################
# Composer
#####################################
# Install the composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


# Clear package lists
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Create application directory
RUN mkdir -p /app
WORKDIR /app

# Copy composer.json
COPY composer.json composer.json

# Install project dependencies
RUN composer install \
    --ignore-platform-reqs \
    --no-interaction \
    --no-plugins \
    --no-scripts \
    --no-autoloader \
    --prefer-dist \
    && rm -rf /root/.composer

EXPOSE 8000