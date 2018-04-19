FROM ubuntu:16.04

# Build depends
RUN apt-get update && apt-get install -y build-essential curl cmake

# PCL depends
RUN apt-get install -y libboost-all-dev libeigen3-dev libflann-dev libvtk6-dev 

# Optional depends
#RUN apt-get install -y libqhull-dev libvtk6-qt-dev libopenni-dev

# PCL 1.8.1
RUN curl -OL https://github.com/PointCloudLibrary/pcl/archive/pcl-1.8.1.tar.gz 

# Build PCL
RUN tar -xf pcl-1.8.1.tar.gz && cd pcl-pcl-1.8.1 && mkdir build && cd build && cmake .. && make -j4 -l4 && make install
