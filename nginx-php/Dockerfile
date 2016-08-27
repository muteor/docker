FROM alpine:latest
MAINTAINER Keith Pope <thepope@thepopeisdead.com>

RUN apk update && apk upgrade && \
    apk add ca-certificates bash && \
    rm -rf /var/cache/apk/*

RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/community/ >> /etc/apk/repositories && \
    apk add --update \
        supervisor nginx php7 php7-fpm \
        php7-zlib php7-mcrypt php7-openssl \
        php7-gd php7-xml php7-json && \
    rm -rf /var/cache/apk/* && \
    mkdir /tmp/nginx && \
    mkdir -p /var/www/html && \
    chown -R nginx:nginx /var/www/html && \
    echo 'date.timezone = "Europe/London"' >> /etc/php7/php.ini && \
    sed -i '/^user/c \user = nginx' /etc/php7/php-fpm.conf && \
    sed -i '/^group/c \group = nginx' /etc/php7/php-fpm.conf && \
    sed -i 's/^listen.allowed_clients/;listen.allowed_clients/' /etc/php7/php-fpm.conf

COPY files/default.conf /etc/nginx/conf.d/
COPY files/nginx.conf /etc/nginx/nginx.conf
COPY files/supervisord.conf /etc/supervisord.conf

EXPOSE 80 443
CMD ["supervisord"]
