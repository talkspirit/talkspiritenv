FROM node:16.20-buster
 
ENV DEBIAN_FRONTEND noninteractive

# to build package
RUN apt-get update && apt-get install -y build-essential debhelper devscripts vim curl sudo libgconf-2-4 apt-transport-https ca-certificates

# Note: this installs the necessary libs to make the bundled version of Chromium that Puppeteer
# installs, work.
RUN apt-get update && apt-get install -y wget --no-install-recommends \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
    && apt-get update \
    && apt-get install -y google-chrome-unstable fonts-ipafont-gothic fonts-wqy-zenhei fonts-thai-tlwg fonts-kacst fonts-freefont-ttf \
      --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get purge --auto-remove -y \
    && rm -rf /src/*.deb

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install -y yarn && ln -sf /usr/share/yarn/bin/yarn /usr/local/bin/yarn

RUN npm install -g grunt-cli grunt jshint

RUN apt-get install -y git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev

RUN curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(rbenv init -)"' >> ~/.bashrc
RUN $HOME/.rbenv/bin/rbenv init -
RUN $HOME/.rbenv/bin/rbenv install 3.2.2
RUN $HOME/.rbenv/bin/rbenv global 3.2.2

RUN echo "gem: --no-document" > ~/.gemrc
RUN "$($HOME/.rbenv/bin/rbenv which gem)"  install bundler

CMD ["bash"]
