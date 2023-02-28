# FROM osrf/ros:noetic-desktop-full
FROM ubuntu:focal

RUN apt-get update

RUN apt-get install -y python3-pip
RUN apt-get install -y git curl
RUN apt-get install -y vim nano

ENV TZ=Europe/Athens
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
ENV DEBIAN_FRONTEND noninteractive
RUN 

RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu focal main" > /etc/apt/sources.list.d/ros-latest.list'
RUN apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -
RUN apt update 
RUN apt -y install ros-noetic-desktop-full
RUN echo "alias python=python3" >> ~/.bashrc
RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
RUN apt -y install ros-noetic-moveit 
RUN apt -y install ros-noetic-moveit-visual-tools ros-noetic-effort-controllers ros-noetic-joint-trajectory-controller

RUN apt -y install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
RUN rosdep init 
RUN rosdep update

RUN python3 -m pip install numpy==1.20.3 open3d

# alias for non-intercive shell commands
RUN echo '#!/usr/bin/python3' > /usr/bin/python && chmod +x /usr/bin/python 
# #!/usr/bin/env python
RUN cd ~ && git clone --branch main3 https://github.com/constant-inos/Workspaces.git
RUN echo "source ~/Workspaces/intrarobots_ws/devel/setup.bash" >> ~/.bashrc

# SHELL ["/bin/bash", "-c"]
RUN /bin/bash -c '. /opt/ros/noetic/setup.bash; bash ~/Workspaces/intrarobots_ws/src/extras/create_packages.sh'
RUN /bin/bash -c '. ~/Workspaces/intrarobots_ws/devel/setup.bash'
RUN /bin/bash -c 'cd /home/ntinos/Workspaces/intrarobots_ws/src/extras && bash update_gazebo_models.sh'


# RUN source ~/.bashrc
# RUN bash ~/Workspaces/intrarobots_ws/src/extras/create_packages.sh 
# RUN echo "source ~/Workspaces/intrarobots_ws/devel/setup.bash" >> ~/.bashrc

# RUN  echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc 
# RUN  echo "source ~/Workspaces/intrarobots_ws/devel/setup.bash" >> ~/.bashrc && source ~/.bashrc

# RUN cd ~/Workspaces/intrarobots_ws && catkin_make

# RUN export https_proxy=http://icache.intracomtel.com:80/
# RUN export http_proxy=http://icache.intracomtel.com:80/


# CMakeLists.txt      moveit_visual_tools
# extras              panda_moveit_config
# franka_description  robotic_arm_descriptions
# geometric_shapes    robotic_arm_gazebo
# master              robotic_arm_moveit
# moveit              robotic_arm_moveit_interface
# moveit_msgs         robots
# moveit_resources    rviz_visual_tools
# moveit_tutorials    srdfdom
