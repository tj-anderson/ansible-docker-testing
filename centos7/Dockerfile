FROM centos:centos7

# Install Ansible and other requirements.
RUN yum makecache fast \
  && yum -y install deltarpm epel-release initscripts \
  && yum -y update \
  && yum -y install \
  ansible \
  sudo \
  which \
  && yum clean all

# Replace systemctl
COPY ./systemctl.py /usr/bin/systemctl
RUN chmod 755 /usr/bin/systemctl

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Install Ansible inventory file.
RUN echo -e '[local]\nlocalhost ansible_connection=local' > /etc/ansible/hosts

ENTRYPOINT [ "/bin/bash" ]