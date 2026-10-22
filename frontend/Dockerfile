FROM node:22.23.4-bookworm

ENV DEBIAN_FRONTEND=noninteractive

# to build package
RUN apt-get update && apt-get install -y build-essential debhelper devscripts vim curl sudo libgconf-2-4 apt-transport-https ca-certificates

# Note: this installs the necessary libs to make the bundled version of Chromium that Puppeteer
# installs, work.
RUN apt-get update \
    && apt-get install -y chromium fonts-ipafont-gothic fonts-wqy-zenhei fonts-thai-tlwg fonts-kacst fonts-freefont-ttf \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get purge --auto-remove -y \
    && rm -rf /src/*.deb

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install -y yarn && ln -sf /usr/share/yarn/bin/yarn /usr/local/bin/yarn

# Playwright 1.39 downloads browsers from playwright.azureedge.net, which no longer
# serves them; point it at Microsoft's current download host instead. Only Chromium
# is still published there for this version (Firefox/WebKit builds return 400).
RUN npm install -g grunt-cli grunt jshint playwright@1.39.0 \
    && PLAYWRIGHT_DOWNLOAD_HOST=https://playwright.download.prss.microsoft.com/dbazure/download/playwright \
    npx playwright install --with-deps chromium

CMD ["bash"]
