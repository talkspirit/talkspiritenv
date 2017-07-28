FROM node:8.2.1

ENV DEBIAN_FRONTEND noninteractive

# to build package
RUN apt-get update && apt-get install -y build-essential debhelper devscripts vim curl sudo

RUN npm install -g grunt-cli grunt jshint

CMD ["bash"]
