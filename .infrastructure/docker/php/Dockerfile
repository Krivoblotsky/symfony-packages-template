FROM php:8.3-cli-alpine

# Install system dependencies
RUN apk add --no-cache \
    git \
    curl \
    libpng-dev \
    libzip-dev \
    zip \
    unzip \
    bash \
    make \
    oniguruma-dev

# Install PHP extensions
RUN docker-php-ext-install \
    mbstring \
    zip \
    pdo_mysql \
    opcache

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /app

# Expose port (default 8000, can be overridden via env)
EXPOSE 8000

# Start PHP built-in server
CMD ["sh", "-c", "php -S 0.0.0.0:${PHP_SERVER_PORT:-8000} -t public"]
