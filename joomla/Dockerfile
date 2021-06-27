FROM debian:buster
RUN apt-get update && apt-get install -y  --no-install-recommends -qqy \
wget \
unzip \
php-fpm \
nginx \
curl \
php \
php-gd \
php-xmlrpc \
php-curl \
php-intl \
php-imagick \
php-mysql \
php-zip \
php-xml \
php-mbstring \
php-bcmath \
ca-certificates && \
wget -O Joomla.zip https://github.com/AFUJ/joomla-cms-fr/releases/download/3.9.15.1/Joomla_3.9.15-Stable-Full_Package_French_v1.zip && \
unzip Joomla.zip -d /var/www/joomla &&\
rm -f /etc/nginx/site-available/* &&\
rm -rf /var/www/html &&\
apt-get clean -qqy && rm -rf /var/lib/apt/*
COPY joomla.local.conf /etc/nginx/conf.d
RUN chown -R www-data:www-data /var/www/joomla
COPY www.conf /etc/php/7.3/fpm/pool.d/www.conf
RUN service php7.3-fpm start
RUN service php7.3-fpm stop
EXPOSE 80
VOLUME /var/www/joomla
ADD start.sh /
RUN chmod +x /start.sh
CMD ["/start.sh"]