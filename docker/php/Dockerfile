# Dockerfile for PHP with WordPress

FROM php:8.0-fpm

# Criação do diretório conf.d
RUN mkdir -p /etc/nginx/conf.d

# Adição para cache
RUN { \
    echo 'fastcgi_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m;'; \
    echo 'fastcgi_cache_key "$scheme$request_method$host$request_uri";'; \
} > /etc/nginx/conf.d/cache.conf

# Exibição de erros
RUN { \
    echo 'display_errors = on'; \
    echo 'display_startup_errors = on'; \
    echo 'error_reporting = E_ALL'; \
} > /usr/local/etc/php/conf.d/custom.ini

# Adição de ajustes de desempenho
ENV MYSQL_OPTS="--innodb_buffer_pool_size=256M"

# Instalação de extensões úteis (por exemplo, PDO, mysqli, mbstring, opcache)
RUN apt-get update \
    && apt-get install -y libpq-dev libonig-dev pkg-config \
    && docker-php-ext-configure pdo_pgsql --with-pdo-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql mysqli mbstring opcache \
    && pecl install mongodb \
    && docker-php-ext-enable mongodb \
    && docker-php-ext-install bcmath # Adicionado para suporte adicional

# Configuração de Timezone
RUN echo "date.timezone = 'America/Sao_Paulo'" > /usr/local/etc/php/conf.d/timezone.ini

# Habilitar Opcache
RUN docker-php-ext-enable opcache

# Instalar WP-CLI (linha de comando do WordPress)
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp

# Limpeza para reduzir o tamanho da imagem
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php-fpm"]
