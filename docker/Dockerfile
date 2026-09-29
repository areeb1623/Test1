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

# Skapa mappar och dokumentfiler permanent för labben
RUN mkdir -p /run/sshd /home/student/dokument && \
    echo "Ekonomirapport 2026" > /home/student/dokument/ekonomi.txt && \
    echo "Kundregister" > /home/student/dokument/kunder.txt && \
    echo "Serverinformation" > /home/student/dokument/serverinfo.txt && \
    echo "Projektplan 2026" > /home/student/dokument/projekt.txt && \
    echo "Personallista" > /home/student/dokument/personal.txt && \
    echo "Installationer" > /home/student/dokument/installationer.txt && \
    chown -R student:student /home/student/dokument && \
    ssh-keygen -A

CMD ["/usr/sbin/sshd", "-D"]