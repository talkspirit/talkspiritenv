FROM node:6.2.1

ENV DEBIAN_FRONTEND noninteractive

# to build package
RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y build-essential debhelper devscripts vim curl sudo

RUN sudo echo "Europe/Paris" > /etc/timezone
RUN sudo dpkg-reconfigure -f noninteractive tzdata

CMD ["bash"]
