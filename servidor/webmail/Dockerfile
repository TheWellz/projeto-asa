FROM php:apache

RUN apt update && apt install -y unzip && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html
RUN curl -sL https://www.rainloop.net/repository/webmail/rainloop-latest.zip -o rainloop.zip \
    && unzip rainloop.zip -d rainloop \
    && rm rainloop.zip \
    && chown -R www-data:www-data rainloop

CMD ["apache2-foreground"]