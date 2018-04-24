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
RUN curl -OL --insecure https://github.com/PointCloudLibrary/pcl/archive/pcl-1.8.1.tar.gz 

# Build PCL
RUN tar -xf pcl-1.8.1.tar.gz && \
    cd pcl-pcl-1.8.1 && \
    mkdir build && cd build && \
    cmake .. && make -j4 && \
    make install && ldconfig && \
    cd ../.. && rm -rf pcl-pcl-1.8.1
