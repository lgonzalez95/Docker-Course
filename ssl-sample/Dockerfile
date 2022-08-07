FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive 

RUN apt-get update && apt-get upgrade -y
RUN apt-get install apache2 php openssl -y

WORKDIR /var/www/html/
COPY html-ssl .

RUN echo "<?php phpinfo(); ?>" > ./test.php

RUN mkdir /etc/apache2/certs
COPY docker.crt /etc/apache2/certs/docker.crt
COPY docker.key /etc/apache2/certs/docker.key

COPY ssl-params.conf /etc/apache2/sites-available/ssl-params.conf
COPY ssl.conf /etc/apache2/sites-enabled/000-default.conf

RUN a2enmod ssl 
RUN a2enmod rewrite 

CMD ["apachectl", "-D", "FOREGROUND"]