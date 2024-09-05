FROM debian:stretch-slim

# install git
RUN apt-get update && \
    apt-get install git -yqq

# initilize ssh key
ADD ssh/id_rsa /root/.ssh/
RUN chmod 600 /root/.ssh/id_rsa && \
    echo "IdentityFile /root/.ssh/id_rsa" >> /etc/ssh/ssh_config && \
    echo "StrictHostKeyChecking no" >> /etc/ssh/ssh_config

# clone app
WORKDIR /home/app
RUN git init && \
    git remote add origin {{ git_base_address }}/server.git && \
    git pull origin {{ deployment_branch }}

# clone admin
WORKDIR /home/site
RUN git init && \
    git remote add origin {{ git_base_address }}/site.git && \
    git pull origin {{ deployment_branch }}

# clone admin
WORKDIR /home/panel
RUN git init && \
    git remote add origin {{ git_base_address }}/panel.git && \
    git pull origin {{ deployment_branch }}