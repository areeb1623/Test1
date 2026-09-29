FROM ubuntu:24.04

RUN apt-get update && apt-get install -y \
    openssh-server \
    rsync \
    sudo \
    iproute2 \
    iputils-ping \
    curl \
    net-tools \
    nano \
    vim \
    dnsutils

RUN useradd -m -s /bin/bash student \
    && echo 'student:student' | chpasswd \
    && usermod -aG sudo student \
    && echo 'student ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/student

RUN mkdir -p /run/sshd && ssh-keygen -A

CMD ["/usr/sbin/sshd", "-D"]