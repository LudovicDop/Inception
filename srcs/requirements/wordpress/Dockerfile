FROM debian:buster
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get -y install wget
RUN apt install vim -y
RUN apt-get update && apt-get install -y \
    php7.3 \
    php7.3-fpm \
    php7.3-mysql \
    mariadb-client
RUN wget https://fr.wordpress.org/wordpress-6.0-fr_FR.tar.gz -P /var/www
RUN cd /var/www && tar -xzf wordpress-6.0-fr_FR.tar.gz && rm wordpress-6.0-fr_FR.tar.gz
RUN		chown -R root:root /var/www/wordpress
COPY conf/www.conf /etc/php/7.3/fpm/pool.d
RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp
COPY conf/auto_config.sh /etc/php/
RUN chmod +x /etc/php/auto_config.sh && ./etc/php/auto_config.sh