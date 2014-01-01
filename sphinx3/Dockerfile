FROM ubuntu:12.04

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -yq install curl
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -yq install gcc
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -yq install bison
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -yq install make

RUN curl http://sourceforge.net/projects/cmusphinx/files/sphinxbase/0.7/sphinxbase-0.7.tar.gz/download -L | tar -xzf - -C /tmp
RUN cd /tmp/sphinxbase-0.7 && ./configure --without-python && make && make install && rm -rf /tmp/sphinxbase-0.7

RUN curl http://sourceforge.net/projects/cmusphinx/files/sphinx3/0.8/sphinx3-0.8.tar.gz/download -L | tar -xzf - -C /tmp
RUN cd /tmp/sphinx3-0.8 && sed -ri 's!heap_t h;!heap_t *h;!' /tmp/sphinx3-0.8/src/libs3decoder/libsearch/vithist.c && ./configure --without-python && make && make install && rm -rf /tmp/sphinx3-0.8
