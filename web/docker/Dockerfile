FROM php:8.3

WORKDIR /var/www/html/app

ENV DEBIAN_FRONTEND noninteractive
ENV TZ=Asia/Tehran

RUN apt update
RUN apt install -y vim curl gettext apt-utils supervisor

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN curl -sLS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer
RUN apt autoclean

COPY start-container /usr/local/bin/start-container
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY php.ini /etc/php/8.3/cli/conf.d/99-avt.ini
RUN chmod +x /usr/local/bin/start-container

EXPOSE 8000

ENTRYPOINT ["start-container"]
