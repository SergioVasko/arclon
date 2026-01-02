FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libzip-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    curl \
 && docker-php-ext-install \
    pdo \
    pdo_mysql \
    zip \
    mbstring \
    exif \
    pcntl \
    bcmath \
    gd

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Install Laravel installer globally + create symlink dynamically
RUN composer global require laravel/installer \
 && BIN_DIR=$(composer global config bin-dir --absolute) \
 && ln -sf "$BIN_DIR/laravel" /usr/local/bin/laravel \
 && chmod +x /usr/local/bin/laravel   # sometimes needed if permissions are odd

WORKDIR /var/www/html
