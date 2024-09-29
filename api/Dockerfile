# Use the official PHP image with PHP-FPM
FROM php:8.2-fpm

# Set working directory
WORKDIR /var/www

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl \
    vim \
    nano \
    libpq-dev \
 && docker-php-ext-configure gd --with-freetype --with-jpeg \
 && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Install Composer globally
COPY --from=composer:2.5 /usr/bin/composer /usr/bin/composer

# Copy existing application directory contents to the working directory
COPY . /var/www

# Set correct permissions for Laravel
RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache \
 && chmod -R 775 /var/www/storage /var/www/bootstrap/cache

# Install PHP dependencies
RUN composer install --no-scripts --no-dev --prefer-dist

# Generate optimized autoload files
RUN composer dump-autoload --optimize

# Expose port 8000 for the Laravel application
EXPOSE 8000

# Start the PHP built-in server (instead of PHP-FPM)
CMD ["php", "-S", "0.0.0.0:8000", "-t", "public"]