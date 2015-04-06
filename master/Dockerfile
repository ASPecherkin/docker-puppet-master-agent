# Master
#
# VERSION               0.0.2

FROM     ubuntu:trusty
MAINTAINER aspecherkin "aspecherkin@gmail.com"

# Make sure the package repository is up to date
RUN apt-get update
RUN apt-get install -y openssh-server wget
# add latest puppet pacakge
RUN  wget --no-check-certificate https://apt.puppetlabs.com/puppetlabs-release-trusty.deb
RUN dpkg -i puppetlabs-release-trusty.deb
# after package install we must update 
RUN apt-get update
RUN apt-get install -y puppetmaster
RUN apt-get install -y nano
RUN mkdir /var/run/sshd 
RUN echo 'root:root' |chpasswd

# Install some puppet modules.
# Installing apache as an example
RUN puppet module install puppetlabs-apache

ADD ./site.pp /etc/puppet/manifests/
RUN chmod +r /etc/puppet/manifests/site.pp

ADD ./start.sh /root/

EXPOSE 22
CMD ["/bin/bash", "/root/start.sh"]
