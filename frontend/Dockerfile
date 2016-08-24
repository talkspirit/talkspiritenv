FROM node:6.4

ENV DEBIAN_FRONTEND noninteractive

# to build package
RUN apt-get update && apt-get install -y build-essential debhelper devscripts vim curl sudo

RUN mkdir /tmp/phantomjs

RUN wget --max-redirect=3 -q -O- https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 | \
    tar -xj -C /tmp/phantomjs \
    && cp /tmp/phantomjs/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs \
    && rm -rf /tmp/*

RUN apt-get install -y ruby
RUN gem install sass
RUN npm install -g bower grunt-cli grunt jshint

CMD ["bash"]
