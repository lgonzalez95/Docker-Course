FROM debian

RUN \
    apt update && \
    apt install -y software-properties-common && \
    apt-add-repository ppa:ondrej/php && \
    apt install -y apache2 && \
    apt install -y php7.4

WORKDIR /var/www/html/

RUN echo "<?php phpinfo(); ?>" > ./test.php

CMD ["apachectl", "-D", "FOREGROUND"]
