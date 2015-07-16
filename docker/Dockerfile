FROM ubuntu:14.04

MAINTAINER David Sánchez Falero <david.sanchez.falero@gmail.com>

RUN groupadd -f machinehub
RUN useradd -m -d /home/machinehub -s /bin/bash -c "Machinhub server" -g machinehub machinehub
RUN su machinehub
RUN echo "machinehub ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/machinehub

# Install tools
RUN apt-get update -y && \
	apt-get install -y python-dev \
	wget \
	git \
	build-essential \
	freecad

RUN wget https://raw.github.com/pypa/pip/master/contrib/get-pip.py
RUN python get-pip.py

ENV USER machinehub
USER machinehub
WORKDIR /home/machinehub
ENV HOME /home/machinehub
RUN mkdir .machinehub
ADD conf/ /home/machinehub/.machinehub/
RUN git clone https://github.com/bq/machinehub.git
WORKDIR /home/machinehub/machinehub
RUN sudo pip install -r requirements.txt
WORKDIR /home/machinehub/machinehub

EXPOSE 80