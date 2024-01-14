ARG ROS_DISTRO
FROM ros:${ROS_DISTRO}

WORKDIR /root

RUN apt-get update -qq \
  && apt-get install -y \
    libjson-c-dev \
    wget \
  && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/mongodb/libbson/releases/download/1.5.3/libbson-1.5.3.tar.gz \
  && tar xzf libbson-1.5.3.tar.gz \
  && cd libbson-1.5.3 \
  && ./configure --prefix=$HOME/deps/libbson \
  && make -j$(grep -c ^processor /proc/cpuinfo) \
  && make install

ENV PKG_CONFIG_PATH=$PKG_CONFIG_PATH:~/deps/libbson/lib/pkgconfig/

RUN git clone https://github.com/Sanic/rosbridge2cpp.git \
  && cd rosbridge2cpp \
  && mkdir build \
  && cd build \
  && cmake .. \
  && make