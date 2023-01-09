FROM ubuntu:18.04

SHELL ["/bin/bash", "-c"]

# install dependencies and tools
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    python3-pip \
    locales \
    libsm6 libxext6 libxrender-dev

# set locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# install python dependencies
#RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.7.2 1
RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install markupsafe==2.0.1 numpy==1.19.5 matplotlib==3.3.4 jupyter==1.0.0 opencv-python==3.4.2.16 opencv-contrib-python==3.4.2.16
#RUN python3 -m pip install tensorflow

# create dir for cvlab stuff
RUN mkdir -p /home/cvlab
WORKDIR "/home/cvlab"

# set default command
CMD jupyter notebook --port=8888 --no-browser --ip=0.0.0.0 --allow-root
