# How to fatpack with docker
#
# docker build -t `whoami`/emacs-build .
# docker run -v `pwd`/..:/emacs-build `whoami`/emacs-build
#

FROM ubuntu:12.04
MAINTAINER Syohei YOSHIDA

RUN apt-get -y update && apt-get -y upgrade

RUN mkdir /emacs

# Install packages
RUN apt-get -y install \
    build-essential autoconf automake texinfo libncurses5-dev libdbus-1-dev autotools-dev  \
    libgnutls-dev libxml2-dev curl \
    && rm -rf /var/lib/apt/lists/*

RUN curl -L http://ftp.jaist.ac.jp/pub/GNU/emacs/emacs-24.3.tar.xz | tar Jxf - \
    && (cd emacs-24.3 && ./configure --without-x --prefix=/home/travis/.emacs.d/versions/emacs-24.3 && make && make install) \
    && (tar JcfP /emacs/emacs-24.3-travis.tar.xz /home/travis/.emacs.d/versions/emacs-24.3)

RUN curl -L http://ftp.jaist.ac.jp/pub/GNU/emacs/emacs-24.4.tar.xz | tar Jxf - \
    && (cd emacs-24.4 && ./configure --without-x --prefix=/home/travis/.emacs.d/versions/emacs-24.4 && make && make install) \
    && (tar JcfP /emacs/emacs-24.4-travis.tar.xz /home/travis/.emacs.d/versions/emacs-24.4)

RUN curl -L http://ftp.jaist.ac.jp/pub/GNU/emacs/emacs-24.5.tar.xz | tar Jxf - \
    && (cd emacs-24.5 && ./configure --without-x --prefix=/home/travis/.emacs.d/versions/emacs-24.5 && make && make install) \
    && (tar JcfP /emacs/emacs-24.5-travis.tar.xz /home/travis/.emacs.d/versions/emacs-24.5)

RUN curl -L http://ftp.jaist.ac.jp/pub/GNU/emacs/emacs-25.1.tar.xz | tar Jxf - \
    && (cd emacs-25.1 && ./configure --without-x --with-modules --prefix=/home/travis/.emacs.d/versions/emacs-25.1 && make && make install) \
    && (tar JcfP /emacs/emacs-25.1-travis.tar.xz /home/travis/.emacs.d/versions/emacs-25.1)

CMD cp /emacs/*.xz /emacs-build
