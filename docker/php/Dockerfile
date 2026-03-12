FROM php:8.3-fpm

# Installation des dépendances système + extensions PHP en une seule couche
RUN apt-get update && apt-get install -y \
        git \
        unzip \
        libicu-dev \
        libzip-dev \
        zip \
        curl \
    && docker-php-ext-install \
        intl \
        pdo \
        pdo_mysql \
        zip \
        opcache \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Installation de Composer depuis l'image officielle
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Dossier de travail
WORKDIR /var/www

CMD ["php-fpm"]