#PHP Apache setup
FROM php:8.5-rc-fpm-alpine3.21

#Install and update system dependencies
RUN apt update -y; apt install -y supervisor apache2 sqlite=3.48.0-r3 sqlite-libs=3.48.0-r3

#Prepare and setup the working directory
WORKDIR /var/www/html/
COPY vsnippet .

#Copy configs
COPY config/supervisord.conf /etc/supervisord.conf
COPY config/apache.conf /etc/apache2/sites-enabled/apache.conf

#Give permission:
RUN chown -R www-data /var/www/html/

EXPOSE 1337

ENTRYPOINT [ "/usr/bin/supervisord", "-c", "/etc/supervisord.conf" ]
