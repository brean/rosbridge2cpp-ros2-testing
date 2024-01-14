ARG ROS_DISTRO
FROM ros:${ROS_DISTRO}

RUN apt-get update -qq \
  && apt-get install -y \
    ros-${ROS_DISTRO}-rosbridge-suite \
  && rm -rf /var/lib/apt/lists/*
