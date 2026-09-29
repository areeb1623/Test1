FROM ubuntu:24.04

RUN apt-get update && apt-get install -y \
    openssh-server \
    rsync \
    borgbackup \
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

# Skapa backupkataloger permanent
RUN mkdir -p /run/sshd /backups/server1 /backups/server2 && \
    chown -R student:student /backups && \
    ssh-keygen -A

CMD ["/usr/sbin/sshd", "-D"]