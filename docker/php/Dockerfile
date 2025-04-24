FROM php:8.2-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl \
    libpq-dev \
    mariadb-client \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    nodejs \
    npm \
    && docker-php-ext-install pdo pdo_mysql

# Install Composer
COPY --from=composer:2.6 /usr/bin/composer /usr/bin/composer



# Set working directory
WORKDIR /var/www

# Copy project files
COPY . .


# Set permissions
RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache

# Expose port
EXPOSE 9000

# Start PHP-FPM
CMD ["php-fpm"]
