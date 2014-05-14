FROM nvellon/base

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN sudo apt-get update
RUN sudo apt-get install -y apache2-utils pkg-config libgnome-keyring-dev

# Clone Node
RUN cd /usr/src && git clone https://github.com/joyent/node.git

# libicu i18n
RUN cd /usr/src/node && svn checkout --force --revision 214189 http://src.chromium.org/svn/trunk/deps/third_party/icu46 deps/v8/third_party/icu46

#--with-icu-path=deps/v8/third_party/icu46/icu.gyp