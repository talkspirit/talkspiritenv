FROM node:4.1

ENV DEBIAN_FRONTEND noninteractive

# to build package
RUN apt-get update && apt-get install -y vim curl sudo git wget unzip python

# Install phantomjs
RUN apt-get install -y build-essential g++ flex bison gperf ruby perl \
  libsqlite3-dev sqlite3 fontconfig libfontconfig1-dev libicu-dev libfreetype6 libfreetype6-dev libssl-dev \
  libpng-dev libqt5webkit5-dev libjpeg-dev python libx11-dev openssl libxext-dev libssl-dev libpng-dev

# dependances to create a debian package
RUN apt-get install -y build-essential debhelper devscripts

RUN \
  cd /tmp/ && \
  git clone git://github.com/ariya/phantomjs.git && \
  cd phantomjs && \
  git checkout 2.0 && \
  ./build.sh --confirm --jobs 1  && \
  mv bin/phantomjs /usr/local/bin/ && \
  rm -Rf /tmp/phantomjs

RUN apt-get autoremove -yqq \
    &&  apt-get clean \

CMD ["bash"]
