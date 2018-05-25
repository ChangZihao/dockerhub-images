FROM ubuntu:16:04

# new a directory for sshd to run
RUN mkdir -p /var/run/sshd

# installing ssh server
RUN apt-get update
RUN apt-get install -y openssh-server wget tmux vim zsh

# installing sudo
# RUN apt-get install -y sudo

# make ssh services use IPv4 to let X11 forwarding work correctly
RUN echo AddressFamily inet >> /etc/ssh/sshd_config

# defining user account imformation
ARG username=czh
ARG userpasswd=czh

# adding user
RUN useradd -ms /bin/bash $username && (echo $username:$userpasswd | chpasswd)

# adding user to sudo group
RUN adduser $username sudo

# setting running application
CMD /usr/sbin/sshd -D
