FROM ubuntu:18.04
MAINTAINER Nishanth Vurumalla

ARG userid
ARG groupid
ARG username

RUN apt-get update && apt-get install -y git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig python software-properties-common nano bc libssl-dev genisoimage 

# RUN apt-get install -y openjdk-7-jdk

RUN apt-get update && apt-get install -y openjdk-8-jdk

# Create the user and groups same as host computer 

RUN groupadd -g $groupid $username \
 && useradd -m -u $userid -g $groupid $username \
 && usermod -aG sudo $username \
 && echo $username >/root/username \
 && echo "export USER="$username >>/home/$username/.gitconfig

#RUN usermod -aG sudo $username

COPY gitconfig /home/$username/.gitconfig

RUN chown $userid:$groupid /home/$username/.gitconfig

ENV HOME=/home/$username
ENV USER=$username
# ENV JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH $JAVA_HOME/bin:$PATH
ENV JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"

ENTRYPOINT tail -f /dev/null
