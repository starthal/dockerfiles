FROM libpcl-xenial:latest

# libpcl-xenial already has our build dependencies: cmake build-essential pkg-config curl

# Dependencies
RUN apt-get install -y --no-install-recommends \
    libatlas-base-dev libjasper-dev libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev 

# OpenCV 3.4.1
RUN curl --insecure -OL https://github.com/opencv/opencv/archive/3.4.1.tar.gz

# Minimal. We only need the basic library and the Qt GUI
RUN tar -xf 3.4.1.tar.gz && \
    cd opencv-3.4.1 && \
    mkdir build && cd build && \
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D BUILD_PYTHON_SUPPORT=OFF \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D INSTALL_C_EXAMPLES=OFF \
        -D INSTALL_PYTHON_EXAMPLES=OFF \
        -D BUILD_EXAMPLES=OFF \
        -D BUILD_NEW_PYTHON_SUPPORT=OFF \
        -D WITH_IPP=OFF \
        -D WITH_V4L=OFF .. && \
    make -j4 && \
    make install && ldconfig && \
    cd ../.. && rm -rf opencv-3.4.1
