FROM nvellon/base

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN cd /tmp
RUN wget http://ftp.ruby-lang.org/pub/ruby/stable-snapshot.tar.gz
RUN tar -xzf stable-snapshot.tar.gz
RUN (cd "$(ls | grep ruby)" && ./configure --disable-install-doc && make && make install)
RUN cd /tmp
RUN rm -Rf "$(ls | grep ruby)"
RUN rm -f stable-snapshot.tar.gz
