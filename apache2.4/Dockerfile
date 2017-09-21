from  alpine:3.6

RUN apk add --update alpine-sdk autoconf automake m4 libtool docbook2x

COPY libexpat-R_2_2_3.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/libexpat-R_2_2_3.tar.gz
RUN cd /tmp/libexpat-R_2_2_3/expat && ./buildconf.sh && ./configure && make && make install

COPY apr-1.6.2.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/apr-1.6.2.tar.gz
RUN cd /tmp/apr-1.6.2/ && ./configure && make && make install
RUN ls -l /usr/local

COPY apr-util-1.6.0.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/apr-util-1.6.0.tar.gz
RUN cd /tmp/apr-util-1.6.0/ && ./configure --with-apr=/usr/local/apr && make && make install

COPY pcre-8.41.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/pcre-8.41.tar.gz
RUN cd /tmp/pcre-8.41/ && ./configure && make && make install

COPY httpd-2.4.27.tar.gz /tmp
RUN cd /tmp && tar xvzf /tmp/httpd-2.4.27.tar.gz
RUN cd /tmp/httpd-2.4.27/ && ./configure && make && make install

ADD httpd.conf /usr/local/apache2/conf/
ADD httpd-vhosts.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf
RUN mkdir /app

CMD ["/usr/local/apache2/bin/httpd", "-D", "FOREGROUND"]O
