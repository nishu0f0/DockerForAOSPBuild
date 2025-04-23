FROM ubuntu:22.04
MAINTAINER Nishanth Vurumalla
LABEL org.opencontainers.image.authors="Nishanth Vurumalla"

ARG userid
ARG groupid
ARG username

RUN apt-get update && DEBIAN_FRONTEND=noninteractive TZ=Asia/Kolkata apt-get -y install tzdata

RUN apt-get update && apt-get install -y git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev libc6-dev lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev g++-multilib tofrodos python3-markdown libxml2-utils xsltproc vim cgpt libxml-simple-perl libssl-dev libncurses5 cpio rsync cmake pkg-config doxygen automake-1.16 tcl sudo python2.7

RUN apt-get update && apt-get install -y software-properties-common && rm -rf /var/lib/apt/lists/* && add-apt-repository ppa:openjdk-r/ppa -y && apt-get update && apt-get install -y openjdk-8-jdk


# Create the user and groups same as host computer 

RUN groupadd -g $groupid $username \
 && useradd -m -u $userid -g $groupid $username \
 && usermod -aG sudo $username \
 && echo $username >/root/username
 

COPY gitconfig /home/$username/.gitconfig

RUN chown $userid:$groupid /home/$username/.gitconfig

ENV HOME=/home/$username
ENV USER=$username
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH

ENTRYPOINT tail -f /dev/null