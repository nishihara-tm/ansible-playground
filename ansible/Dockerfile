FROM python:3.8

COPY .ssh /root/.ssh
# Install Ansible and dependencies
RUN apt-get update && \
    apt-get install -y ansible ssh && \
    rm -rf /var/lib/apt/lists/*

# Set up SSH keys
RUN mkdir -p /root/.ssh && \
    chmod 700 /root/.ssh && \
    chmod 600 /root/.ssh/id_rsa

# Copy Ansible inventory and playbook
COPY inventory.yml /etc/ansible/hosts
COPY playbook.yml /playbook.yml

# Define the default command
# CMD ["ansible-playbook", "/playbook.yml"]