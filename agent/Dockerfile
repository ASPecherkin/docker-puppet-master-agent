# Agent
#
# VERSION               0.0.2

FROM     ubuntu:trusty
MAINTAINER aspecherkin "aspecherkin@gmail.com"

# make sure the package repository is up to date
RUN apt-get update
RUN apt-get install -y openssh-server wget
# get latest puppet
RUN  wget --no-check-certificate https://apt.puppetlabs.com/puppetlabs-release-trusty.deb
RUN dpkg -i puppetlabs-release-trusty.deb
# after install package we must update
RUN apt-get update
RUN apt-get install -y puppet
RUN apt-get install -y nano
RUN mkdir /var/run/sshd 
RUN echo 'root:root' |chpasswd

ADD ./start.sh /root/

EXPOSE 22
CMD ["/bin/bash", "/root/start.sh"]
