FROM libpcl-xenial:latest

RUN apt-get update

# Build depends
RUN apt-get install -y --no-install-recommends \
    build-essential curl cmake git pkg-config 

RUN apt-get install -y --no-install-recommends \
    libatlas-base-dev gfortran libjasper-dev libgtk2.0-dev libavcodec-dev libavformat-dev ibswscale-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libv4l-dev

RUN curl -OL https://github.com/opencv/opencv/archive/3.4.1.tar.gz
RUN tar -xf 3.4.1.tar.gz && cd opencv-3.4.1 && mkdir build 

WORKDIR /opencv-3.4.1/build
RUN cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D BUILD_PYTHON_SUPPORT=OFF \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D INSTALL_C_EXAMPLES=ON \
	-D INSTALL_PYTHON_EXAMPLES=OFF \
	-D BUILD_EXAMPLES=ON \
	-D BUILD_NEW_PYTHON_SUPPORT=OFF \
	-D WITH_IPP=OFF \
	-D WITH_V4L=ON ..
RUN make -j4
RUN make install && ldconfig
