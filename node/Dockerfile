FROM ubuntu:jammy

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update
RUN apt-get install vim -y
RUN apt-get install curl -y
RUN apt-get install npm -y
RUN apt-get install nmap -y

RUN mkdir -p /var/app/
WORKDIR /var/app/

CMD ["/bin/bash"]
