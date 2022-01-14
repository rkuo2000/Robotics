---
layout: post
title: 機器人作業系統
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

The Robot Operating System(ROS) is a set of software libraries and tools that help you build robot applications.

---
## ROS Introduction
**Paper:** [A ROS2 based communication architecture for control in collaborative and intelligent automation systems](https://arxiv.org/abs/1905.09654)<br>
**ROS** is a collection of tools and libraries that aids robotics software development. Software is written in form of nodes that exchange messages using a transport layer called **TCPROS** based on standard TCP/IP sockets.

ROS has a centralized network configuration which means that there has to exist a running ROS master. 
The master takes care of naming and registration services so that other ROS nodes could find each other on the network
and communicate in a peer-to-peer fashion. Having a configuration where all nodes depend on a central ROS master
is not robust, especially if nodes in a network are distributed on several computers. 

To improve on this design limitation, developers of **ROS2** implemented Object Management Group’s standard **DDS** as the communication middleware considering it to be scalable, robust and well-proven in mission-critical systems.

![](https://images.deepai.org/converted-papers/1903.05850/figures/station.jpg)
An Automated Guided Vehicle (AGV) carrying a diesel truck engine and an autonomous mobile platform (MiR100) carrying kitted material to be assembled on an engine enter the Collaborative Robot Assembly Station. 
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ROS2%20high-level%20communication%20overview.png?raw=true)
<br>

There are several ways to organize nodes, hubs, messages and topics in a distributed ROS system. 
![](https://d3i71xaburhd42.cloudfront.net/402e1ddcb55d584722bbe32f67a87a905f64afb0/7-Figure3-1.png)
(a) Distributor and collector node aided hub oriented communication; (b) Direct hub oriented communication

**Multi-Hub system**<br>

![](https://d3i71xaburhd42.cloudfront.net/402e1ddcb55d584722bbe32f67a87a905f64afb0/7-Figure4-1.png)
(a) Direct node type oriented communication; (b) State collector hub aided node type oriented communication

**TurtleBot**<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ROS%20Robot%20System%20Diagram.png?raw=true)
![](https://emanual.robotis.com/assets/images/platform/turtlebot3/overview/turtlebot3_with_logo.png)
[TurtleBot3 手冊](https://github.com/ROBOTIS-GIT/turtlebot3)<br>

---
### [ROS](https://www.ros.org/)
ROS is released as distributions, also called “distros”<br>
* ROS **Noetic Ninjemys** on Ubuntu Linux (Recommended for Latest ROS 1 LTS) [Install](http://wiki.ros.org/noetic/Installation/Ubuntu)
* ROS **Foxy Fitzroy** on Ubuntu Linux, macOS, or Windows 10 (Recommended for Latest ROS 2 LTS) [Install](https://docs.ros.org/en/foxy/Installation.html)
* ROS **Galactic Gechelone** on Ubuntu Linux, macOS, or Windows 10 (Recommended for Latest ROS 2) [Install](https://docs.ros.org/en/galactic/Installation.html)

[other distributions](https://docs.ros.org/)<br>
<table>
<tr>
<td>Noetic Ninjemys</td>
<td>Foxy Fitzroy</td>
<td>Galactic Gechelone</td>
</tr>
<tr>
<td><img width="200" height="200" src="https://www.ros.org/imgs/noetic.png"></td>
<td><img width="200" height="200" src="https://www.ros.org/imgs/foxy.png"></td>
<td><img width="200" height="200" src="https://www.ros.org/imgs/galactic.png"></td>
</tr>
</table>

### [ROS on DDS](https://design.ros2.org/articles/ros_on_dds.html)
The Data Distribution Service (DDS) for real-time systems is an [Object Management Group (OMG)](https://www.omg.org/) machine-to-machine (sometimes called middleware or connectivity framework) standard that aims to enable dependable, high-performance, interoperable, real-time, scalable data exchanges using a publish–subscribe pattern.

DDS addresses the needs of applications like aerospace and defense, air-traffic control, autonomous vehicles, medical devices, robotics, power generation, simulation and testing, smart grid management, transportation systems, and other applications that require real-time data exchange.

DDS has been used in:
* battleships
* large utility installations like dams
* financial systems
* space systems
* flight systems
* train switchboard systems

**[DDSI-RTPS](https://www.omg.org/spec/DDSI-RTPS/About-DDSI-RTPS/)**<br>
DDSI: DDS Interoperability Wire Protocol
RTPS: Real-Time Publish-Subscribe protocol
The DDS interoperability demonstration used scenarios such as:

* Basic connectivity to network using Internet Protocol (IP)
* Discovery of publishers and subscribers
* Quality of service (QoS) Compatibility between requester and offerer
* Delay-tolerant networking
* Multiple topics and instances of topics
* Exclusive ownerships of topics
* Content filtering of topic data including time and geographic

In 2004, the Object Management Group (OMG) published DDS version 1.0.

**[Object Management Group (OMG)](https://www.omg.org/)**<br>
Founded in 1989 by eleven companies (including Hewlett-Packard, IBM, Sun Microsystems, Apple Computer, American Airlines, iGrafx, and Data General), OMG's initial focus was to create a heterogeneous distributed object standard

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c2/Notional_OMG_DDS_Interoperability.jpg/530px-Notional_OMG_DDS_Interoperability.jpg)
OMG Data Distribution Service interoperability

**Popular DDS vendors include:**<br>
* RTI
* ADLINK Technologies
* Twin Oaks Software

---
## ROS Installation
### [Building ROS 2 on Ubuntu Linux](https://docs.ros.org/en/galactic/Installation/Ubuntu-Development-Setup.html)
**check for UTF-8**<br>
`locale` <br>

**Add the ROS2 apt repository**<br>
`apt-cache policy | grep universe`<br>
500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64

if above output are not seen, then:<br>
`sudo apt install software-properties-common`<br>
`sudo add-apt-repository universe`<br>

Now add the ROS2 apt repository to your system.<br>
`sudo apt update && sudo apt install curl gnupg lsb-release`<br>
`sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg`<br>

Then add the respository to your sources list.<br>
`echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null`

**Install development tools and ROS tools**<br>
```
sudo apt update && sudo apt install -y \
  build-essential \
  cmake \
  git \
  python3-colcon-common-extensions \
  python3-flake8 \
  python3-pip \
  python3-pytest-cov \
  python3-rosdep \
  python3-setuptools \
  python3-vcstool \
  wget
# install some pip packages needed for testing
python3 -m pip install -U \
  flake8-blind-except \
  flake8-builtins \
  flake8-class-newline \
  flake8-comprehensions \
  flake8-deprecated \
  flake8-docstrings \
  flake8-import-order \
  flake8-quotes \
  pytest-repeat \
  pytest-rerunfailures \
  pytest \
  setuptools
```

**Install dependencies using rosdep**<br>
```
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-5.3.1 urdfdom_headers"
```

**Fast DDS library installation**<br>
`sudo apt install libasio-dev libtinyxml2-dev`<br>
`sudo apt install libssl-dev`<br>
`sudo apt install libp11-dev libengine-pkcs11-openssl`<br>
`sudo apt install softhsm2`<br>
`sudo apt install libengine-pkcs11-openssl`<br>

`p11-kit list-modules`<br>
`openssl engine pkcs11 -t`<br>

**Install additional DDS implementations (optional)**<br>
If you would like to use another DDS or RTPS vendor besides the default, Eclipse Cyclone DDS, 
you can find instructions [here](https://docs.ros.org/en/galactic/Installation/DDS-Implementations.html).

**Using ROS1 bridge**<br>
The ROS 1 bridge can connect topics from ROS 1 to ROS 2 and vice-versa.<br> 
See the dedicated [documentation](https://github.com/ros2/ros1_bridge/blob/master/README.md) on how to build and use the ROS 1 bridge.

**Additional RMW implementation (optional)**<br>
The default middleware that ROS 2 uses is **Cyclone DDS**, but the middleware (RMW) can be replaced at runtime.<br>
See the [guide](https://docs.ros.org/en/galactic/How-To-Guides/Working-with-multiple-RMW-implementations.html) on how to work with multiple RMWs.

**Missing Installations**<br>
`sudo apt install libacl1-dev`<br>
`sudo apt install ogre-1.12-tools`<br>
`sudo apt install libxaw7-dev libxt-dev`<br>
`sudo apt install libeigen3-dev`<br>
`cd /usr/include`<br>
`sudo ln -s /usr/include/eigen3/Eigen Eigen`<br>
`sudo apt-get install liblog4cxx-dev`<br>

`pip install catkin_pkg`<br>
`pip install empy`<br>
`pip install lark`<br>
`pip3 install PyQt5`<br>

**Get ROS2 node**<br>
Create a worksapce and clone all repos:
```
mkdir -p ~/ros2_galactic/src
cd ~/ros2_galactic
wget https://raw.githubusercontent.com/ros2/ros2/galactic/ros2.repos
vcs import src < ros2.repos
```

**Build code in a workspace**<br>
`cd ~/ros2_galactic/`<br>
`colcon build --symlink-install`<br>

**Environment setup**<br>
`~/ros2_galactic/install/local_setup.bash`<br>

**Try examples**<br>
Open a terminal:<br>
`ros2 run demo_nodes_cpp talker`<br>

Open another terminal:<br>
`ros2 run demo_nodes_py listener`<br>

![](https://i0.wp.com/pic4.zhimg.com/v2-a6614b68de96fe08698567c2762ce143_r.jpg)

**To Uninstall**<br>
`rm -rf ~/ros2_galactic`<br>

---
## [Gym-Gazebo](https://github.com/erlerobot/gym-gazebo)
an extension of the initial OpenAI gym for robotics using ROS and Gazebo<br>

GazeboCircuit2TurtlebotLidar-v0

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboCircuit2TurtlebotLidar-v0.png?raw=true)

GazeboCircuitTurtlebotLidar-v0

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboCircuitTurtlebotLidar-v0.png?raw=true)

GazeboCartPole-v0

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/cartpole.jpg?raw=true)

GazeboModularArticulatedArm4DOF-v1

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularArticulatedArm4DOF-v1.jpg?raw=true)

GazeboModularScara4DOF-v3

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara4DOF-v3.png?raw=true)

GazeboModularScara3DOF-v3

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara3DOF-v3.png?raw=true)

GazeboModularScara3DOF-v2

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara3DOF-v2.png?raw=true)

ARIACPick-v0

![](https://github.com/erlerobot/gym-gazebo/blob/master/imgs/ariac_pick.jpg?raw=true)

---
### RDS
**[ROS Developement Studio](https://www.theconstructsim.com/)**<br>
![](https://www.theconstructsim.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-10-at-17.08.49-1024x486.png)

**[exploring-ros-2-wheeled-robot-part-01](https://www.theconstructsim.com/exploring-ros-2-wheeled-robot-part-01/)**<br>
![](https://www.theconstructsim.com/wp-content/uploads/2019/04/m2wr_gazebo.png)

---
### ROS2 ESP32
**Code:** [shirokunet/ros2_esp32bot](https://github.com/shirokunet/ros2_esp32bot)<br>
![](https://camo.githubusercontent.com/c7ee71399d568f5c97d8ca756219ebb68d3e103bd13128aa796e0dc221d80b6b/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f7835734b45765f525168476d357143432d7a44466d46394d662d374b35577a506a704753575675765063647052715a4d4b6852634b344a5347366e36763844505434686c79576a6d4261437057565847535773667254553750326f7975305839576e65766e4667516c6c5579616547776857457846536451787243566f6c6e2d4a6f725a6944764d3041)

**Blog:** [如何使用esp32從零制作一個ROS2的teleop遙控器](https://chowdera.com/2021/10/20211023102532530v.html)<br>

![](https://inotgo.com/imagesLocal/202110/23/20211023102200379D_5.jpg)

**Blog:** [Setting up an ESP32 microcontroller for ROS2 robotics](https://blog.hadabot.com/set-up-esp32-microcontroller-for-ros2-robotics.html)<br>
![](https://blog.hadabot.com/images/hadabot_teleop__controller_01.jpg)

**Blog:** [micro-ROS porting to ESP32](https://discourse.ros.org/t/micro-ros-porting-to-esp32/16101)<br>
[core tutorials](https://micro.ros.org//docs/tutorials/core/overview/)<br>

```
ros2 run micro_ros_setup create_firmware_ws.sh freertos esp32

ros2 run micro_ros_setup configure_firmware.sh int32_publisher -t udp -i [your local machine IP] -p 8888

ros2 run micro_ros_setup build_firmware.sh menuconfig

# Now go to the micro-ROS Transport Settings → WiFi Configuration menu and fill your WiFi SSID and password. Save your changes, exit the interactive menu, and run:

ros2 run micro_ros_setup build_firmware.sh

# Connect your ESP32 to the computer with a micro-USB cable, and run:

ros2 run micro_ros_setup flash_firmware.sh
```

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

