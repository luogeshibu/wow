FROM ubuntu:16.04

LABEL maintainer "shibu.luoge@harman.com"

ARG DEBIAN_FRONTEND=noninteractive


# Basic
RUN apt-get update && apt-get install -y curl sudo net-tools vim openjdk-8-jdk iputils-ping openssh-server wget build-essential libssl-dev libffi-dev python-dev 
RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash

# Harman
RUN apt-get install -y  build-essential checkinstall doxygen asciidoc avr-libc automake android-tools-fsutils \
                        gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential git-lfs \
                        socat cpio python python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping perl cmake make \
                        corkscrew  libsdl1.2-dev dnsutils libterm-readkey-perl g++ libsdl2-dev \
                        lzop liblz4-tool mc rpm libboost1.58-tools-dev  

# install pip on ubuntu 16.04
RUN wget https://bootstrap.pypa.io/pip/3.5/get-pip.py -P /root && python3 /root/get-pip.py && rm /root/get-pip.py

# install python module
RUN pip install Cryptography

######## This is for customize the comtainer for user
# install openjdk 11 for jenkins remote via ssh.
RUN mkdir -p /opt/openjdk/openjdk-11 && \
    wget https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_linux-x64_bin.tar.gz -P /opt/openjdk/openjdk-11 && \
    tar -xzvf /opt/openjdk/openjdk-11/openjdk-11.0.2_linux-x64_bin.tar.gz -C /opt/openjdk/openjdk-11 && \
    rm -rf /opt/openjdk/openjdk-11/openjdk-11.0.2_linux-x64_bin.tar.gz

# setting svc_cpmshint account for git configuration 
RUN wget http://10.80.105.183/download/docker/svc_cpmshint_ssh.tar.gz -P /root && tar -xzvf /root/svc_cpmshint_ssh.tar.gz -C /root/ && \
    mv /root/ssh /root/.ssh && cp /root/.ssh/gitconfig  /root/.gitconfig && rm /root/svc_cpmshint_ssh.tar.gz

# Setting sshd service for permit root login and change root password
RUN sed -i 's/^PermitRootLogin/#&/' /etc/ssh/sshd_config && echo "PermitRootLogin yes" >> /etc/ssh/sshd_config && echo 'root:123456' | chpasswd 

# install harman repo command for the container.
RUN curl -SL http://10.80.105.183/download/docker/repo -o /usr/bin/repo && chmod +x /usr/bin/repo

# start sshd service when container start
RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
