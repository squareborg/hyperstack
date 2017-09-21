from  alpine:3.6

RUN apk add --update alpine-sdk autoconf automake m4 libtool docbook2x libcurl curl-dev libpng libpng-dev libmcrypt libmcrypt-dev zlib zlib-dev

COPY libxml2-2.9.4.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/libxml2-2.9.4.tar.gz
RUN cd /tmp/libxml2-2.9.4/ && ./configure && make && make install

COPY php-7.1.8.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/php-7.1.8.tar.gz
RUN cd /tmp/php-7.1.8/ && ./configure --enable-fpm --with-mysqli --with-curl --with-mcrypt --with-gd --with-zlib-dir=/usr && make && make install
COPY php-fpm.conf /usr/local/etc/php-fpm.conf
COPY pools.conf /usr/local/etc/php-fpm.d/pools.conf
COPY php.ini /usr/local/lib/php.ini
RUN cp /tmp/php-7.1.8/sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
RUN chmod +x /etc/init.d/php-fpm
RUN adduser -D app
RUN mkdir /app
RUN chown app:app /app
EXPOSE 9001
CMD ["/usr/local/sbin/php-fpm","--nodaemonize","--fpm-config","/usr/local/etc/php-fpm.conf","--pid","/usr/local/var/run/php-fpm.pid"]

