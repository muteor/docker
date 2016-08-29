FROM muteor/linkerd-base

# Fix TERM warnings
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Keith Pope <thepope@thepopeisdead.com>

RUN apt-get update -q && \
    echo "deb http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list && \
    echo "deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list && \
    wget http://www.dotdeb.org/dotdeb.gpg && \
    apt-key add dotdeb.gpg && \
    apt-get update -q && \
    apt-get install -yq supervisor nginx php7.0 php7.0-fpm \
         php7.0-mcrypt php7.0-gd php7.0-json && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir /tmp/nginx && \
    mkdir -p /var/www/html && \
    mkdir -p /etc/linkerd/disco && \
    mkdir -p /var/log/linkerd && \
    chown -R www-data:www-data /var/www/html && \
    echo 'date.timezone = "Europe/London"' >> /etc/php/7.0/fpm/php.ini

COPY files/default /etc/nginx/sites-available
COPY files/supervisord.conf /etc/supervisord.conf

EXPOSE 80 443
CMD ["supervisord", "-c", "/etc/supervisord.conf"]
