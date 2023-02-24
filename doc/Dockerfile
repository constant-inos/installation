FROM osrf/ros:noetic-desktop
# FROM ubuntu:focal

RUN apt-get update

RUN apt-get install -y python3-pip
RUN apt-get install -y git
RUN apt-get install -y vim nano

RUN git clone https://github.com/constant-inos/installation.git
RUN cp installation/xslocobot_amd64_install_ni.sh xslocobot_amd64_install.sh

RUN export https_proxy=http://icache.intracomtel.com:80/
RUN export http_proxy=http://icache.intracomtel.com:80/

RUN chmod +x xslocobot_amd64_install.sh
RUN ./xslocobot_amd64_install.sh -d noetic -b create3 -n

