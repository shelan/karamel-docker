# sshd
#
# VERSION               0.0.2

#FROM phusion/baseimage:0.9.15
FROM ubuntu:14.04
MAINTAINER Shelan Perera <shelanrc@gmail.com>
RUN useradd --create-home --shell /bin/bash vagrant
RUN echo root:vagrant | chpasswd
RUN echo vagrant:vagrant | chpasswd

ADD https://raw.githubusercontent.com/mitchellh/vagrant/master/keys/vagrant.pub /home/vagrant/.ssh/authorized_keys
RUN chown -R vagrant:vagrant /home/vagrant/.ssh
RUN chmod 0600 /home/vagrant/.ssh/authorized_keys
RUN chmod 0700 /home/vagrant/.ssh

RUN apt-get update
RUN apt-get -y install curl build-essential libxml2-dev libxslt-dev git
RUN apt-get install -y openssh-server

#RUN curl -L https://www.opscode.com/chef/install.sh | bash
#RUN echo "gem: --no-ri --no-rdoc" > ~/.gemrc
#RUN /opt/chef/embedded/bin/gem install berkshelf
#RUN apt-get clean

#RUN echo "export PATH=/opt/chef/embedded/bin:$PATH" >> /etc/bash.bashrc
#RUN echo "export PATH=/opt/chef/embedded/bin:$PATH" >> /home/vagrant/.bashrc
#RUN echo "export PATH=/opt/chef/embedded/bin:$PATH" >> /root/.bashrc

#RUN ln -s /opt/chef/embedded/bin/berks /usr/bin/berks

RUN curl -L https://opscode-omnibus-packages.s3.amazonaws.com/ubuntu/12.04/x86_64/chefdk_0.6.2-1_amd64.deb -o chefdk_0.6.2-1_amd64.deb
RUN dpkg -i chefdk_0.6.2-1_amd64.deb
RUN rm -rf chefdk_0.6.2-1_amd64.deb

RUN \
  apt-get update && \
  apt-get install -y openjdk-7-jdk && \
  rm -rf /var/lib/apt/lists/*
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
RUN apt-get clean

RUN mkdir /var/run/sshd
CMD ["/usr/sbin/sshd", "-D", "-e"]
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ADD sudoers.d/01_vagrant /etc/sudoers.d/
RUN chmod 0440 /etc/sudoers.d/01_vagrant
RUN usermod -a -G root vagrant


EXPOSE 22