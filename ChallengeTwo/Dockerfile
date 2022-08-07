FROM debian

RUN \
    apt update && \
    apt install -y software-properties-common && \
    apt-add-repository ppa:ondrej/php && \
    apt install -y apache2 && \
    apt install -y php7.4

CMD ["apachectl", "-D", "FOREGROUND"]