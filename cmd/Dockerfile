FROM richarvey/nginx-php-fpm:2.1.2

WORKDIR /var/www/html/
COPY . .

# Image config
ENV SKIP_COMPOSER 1
ENV WEBROOT /var/www/html/public
ENV PHP_ERRORS_STDERR 1
ENV RUN_SCRIPTS 1
ENV REAL_IP_HEADER 1

# Laravel config
ENV APP_ENV production
ENV APP_DEBUG false
ENV LOG_CHANNEL stderr

# Laravel config - testing db
ENV DB_CONNECTION sqlite
ENV DB_DATABASE /var/www/html/database.sqlite

# Allow composer to run as root
ENV COMPOSER_ALLOW_SUPERUSER 1

# [temporary] Set permission for db file
RUN ["touch", "./database.sqlite"]
RUN ["chmod", "a+r+w", "./database.sqlite"]

RUN ["pwd"]
RUN ["chmod", "+x", "./cmd/start.sh"]
RUN ["./cmd/start.sh"]

CMD ["php", "artisan", "serve"]
