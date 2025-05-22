FROM php:8.1-fpm

RUN apt-get update && apt-get install -y \
    git unzip libzip-dev zip libonig-dev libpng-dev libjpeg-dev libfreetype6-dev libxml2-dev curl \
    && docker-php-ext-install pdo_mysql zip exif pcntl bcmath gd

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

COPY . .

RUN composer install --no-dev --optimize-autoloader

RUN chown -R www-data:www-data storage bootstrap/cache

EXPOSE 9000

CMD ["php-fpm"]
