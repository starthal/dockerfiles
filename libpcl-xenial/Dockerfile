FROM ubuntu:16.04

RUN apt-get update

# Build depends
RUN apt-get install -y --no-install-recommends \
    build-essential curl cmake

# PCL depends
RUN apt-get install -y --no-install-recommends \
    libboost-all-dev libeigen3-dev libflann-dev libvtk6-dev libproj-dev

# Optional depends
#RUN apt-get install -y libqhull-dev libvtk6-qt-dev libopenni-dev

# PCL 1.8.1
RUN curl -OL https://github.com/PointCloudLibrary/pcl/archive/pcl-1.8.1.tar.gz 

# Build PCL
RUN tar -xf pcl-1.8.1.tar.gz && cd pcl-pcl-1.8.1 && mkdir build
WORKDIR pcl-1.8.1/build
RUN cmake .. 
RUN make -j4 && make install
RUN make install && ldconfig
