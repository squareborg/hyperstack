from  alpine:3.6

RUN apk add --update alpine-sdk autoconf automake m4 libtool docbook2x cmake ncurses5-libs

RUN cd /tmp/ && git clone https://github.com/MariaDB/server.git
RUN mkdir /tmp/build-mariadb
RUN cd /tmp/build-mariadb && cmake -DCURSES_LIBRARY=/usr/lib/libncurses.so.5 -DCURSES_INCLUDE_PATH=/usr/include ../server
#RUN cd /tmp/server-mariadb-10.2.7/ && ./configure && make && make install

