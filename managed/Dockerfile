FROM ubuntu:20.04

# Set up SSH server
RUN apt-get update && \
    apt-get install -y openssh-server && \
    rm -rf /var/lib/apt/lists/*
RUN mkdir /run/sshd

# Create a user
RUN echo 'root:root' | chpasswd && \
    sed -i "s/#PermitRootLogin prohibit-password/PermitRootLogin yes/" /etc/ssh/sshd_config && \
    sed -i "s/#PubkeyAuthentication yes/PubkeyAuthentication yes/" /etc/ssh/sshd_config

RUN mkdir /root/.ssh && \
    touch /root/.ssh/authorized_keys && \
    chmod 700 /root/.ssh && \
    chmod 600 /root/.ssh/authorized_keys

# Set up SSH keys
COPY .ssh/id_rsa.pub /root/.ssh/authorized_keys

EXPOSE 22

# Define the default command
CMD ["/usr/sbin/sshd", "-D"]