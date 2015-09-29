FROM debian:8.2
MAINTAINER Olivier RICARD <olivier+docker@talkspirit.com>

RUN apt-get update \
    && apt-get install -y \
        build-essential \
        curl \
        g++ \
        flex \
        bison \
        gperf \
        ruby \
        perl \
        python \
        libsqlite3-dev \
        libfontconfig1-dev \
        libicu-dev \
        libfreetype6 \
        libssl-dev \
        libpng-dev \
        libjpeg-dev \
        libqt5webkit5-dev \
    && curl -L https://github.com/ariya/phantomjs/archive/2.0.0.tar.gz | tar -xzC /tmp \
    && cd /tmp/phantomjs-2.0.0 \
    && ./build.sh --confirm --silent --jobs 2 \
    && mv bin/phantomjs /usr/local/bin \
    && cd \
    && apt-get purge --auto-remove -y \
        build-essential \
        curl \
        g++ \
        flex \
        bison \
        gperf \
        ruby \
        perl \
        python \
    && apt-get clean \
    && rm -rf /tmp/* /var/lib/apt/lists/*


CMD ["bash"]
