#Run fwbuilder in a container
#
#
# docker run -d  \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-e DISPLAY=unix$DISPLAY \
#	fwbuilder
#
#

FROM centos:6
MAINTAINER Jodie Cunningham <jodie.cunningham@gmail.com>


RUN yum update -y && yum install wget xorg-x11-fonts-Type1 -y
RUN wget "ftp://ftp.pbone.net/mirror/ftp.sourceforge.net/pub/sourceforge/f/fw/fwbuilder/Current_Packages/5.1.0/fwbuilder-5.1.0.3599-1.el6.x86_64.rpm"
RUN yum localinstall fwbuilder-5.1.0.3599-1.el6.x86_64.rpm -y

RUN useradd -s `which nologin` -c '' -U fwbuilderuser

USER fwbuilderuser
ENTRYPOINT ["/usr/bin/fwbuilder"]
