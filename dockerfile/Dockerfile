FROM continuumio/miniconda3

MAINTAINER "Carlos H Brandt <carloshenriquebrandt.gmail>"

# Install PDAL - https://pdal.io/index.html
#
RUN conda install --yes --channel conda-forge pdal

# Install LAStools: http://lastools.org/download/LAStools.zip
# LAStools has some (non-free, I guess) license attached to it, so I decided
# not to include in this repo. It is then assumed that there will be a
# directory "./LAStools" in this context.
#
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update &&\
    apt-get install -y unzip make cmake gcc g++ &&\
    apt-get clean

ADD LAStools/LAStools.zip /tmp/.

RUN cd /tmp && unzip LAStools.zip && cd LAStools && rm -rf bin/* &&\
    make                                                          &&\
    mv bin/* /usr/local/bin                                       &&\
    cd /tmp && rm -rf LAStools*

# Add our special entrypoint
#
RUN git clone -b stable https://github.com/chbrandt/docker_commons.git && \
    ln -sf docker_commons/entrypoint.sh /.

ENTRYPOINT ["/entrypoint.sh"]
