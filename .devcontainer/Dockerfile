FROM ghcr.io/nasa/astrobee:latest-ubuntu20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        openssh-server \
        ca-certificates \
        procps && \
    mkdir -p /run/sshd && \
    ssh-keygen -A && \
    sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication no/' /etc/ssh/sshd_config && \
    sshd -t && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND=dialog
