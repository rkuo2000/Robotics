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

**ROS** has a centralized network configuration which means that there has to exist a running ROS master. 
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

---
### [Robots using ROS](http://library.isr.ist.utl.pt/docs/roswiki/Robots.html)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/Robots_using_ROS.png?raw=true)

---
### TurtleBot
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ROS%20Robot%20System%20Diagram.png?raw=true)
[TurtleBot3 手冊](https://github.com/ROBOTIS-GIT/turtlebot3)<br>
![](https://emanual.robotis.com/assets/images/platform/turtlebot3/overview/turtlebot3_with_logo.png)

---
## [ROS](https://www.ros.org/) distros
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
## Ubuntu20.04 on Windows 10/11

### WSL install Ubuntu20.04
[WSL 的基本命令](https://docs.microsoft.com/zh-tw/windows/wsl/basic-commands)<br>

* Open **PowerShell** as administrator (管理者權限)<br>
```
wsl --status
wsl --update
wsl --shutdown
```

**For Disk C:**
```
wsl --install -d ubuntu
```

[Installing WSL Distro to a different/custom location](https://vpraharsha3.medium.com/installing-wsl-distro-to-a-different-custom-location-30d101f04113)<br> 
**For Disk D:** 
* Open **PowerShell** as administrator (管理者權限)<br>
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
* Create D:\WSL directory
```
Set-Location D:
New-Item WSL -ItemType Directory
Set-Location .\WSL
```
* Download Ubuntu.appx 
```
Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile Ubuntu.appx -UseBasicParsing
```
> Available Distros:<br>
> Ubuntu 20.04 - https://aka.ms/wslubuntu2004<br>
> Ubuntu 20.04 ARM - https://aka.ms/wslubuntu2004arm<br>
> Ubuntu 18.04 - https://aka.ms/wsl-ubuntu-1804<br>
> Ubuntu 18.04 ARM - https://aka.ms/wsl-ubuntu-1804-arm<br>
> Ubuntu 16.04 - https://aka.ms/wsl-ubuntu-1604<br>
> Debian GNU/Linux - https://aka.ms/wsl-debian-gnulinux<br>
> Kali Linux - https://aka.ms/wsl-kali-linux-new<br>
> OpenSUSE Leap 42 - https://aka.ms/wsl-opensuse-42<br>
> SLES - https://aka.ms/wsl-sles-12<br>

* rename Ubuntu.appx to .zip & unzip it
```
Rename-Item .\Ubuntu.appx Ubuntu.zip
Expand-Archive .\Ubuntu.zip -Verbose
```

* Go to Folder D:\WSL\Ubuntu, run **ubuntu_2004.2021.825.0_x64.appx** as adminstrator(管理者權限)<br>
```
installing, this may take a few minutes...
Enter new UNIX username: yourname 
Enter new UNIX password: **** 
Retype new UNIX password: ****
passwd: password updated successfully
Installation successful!
```
* Ubuntu update & upgrade
```
sudo apt update
sudo apt upgrade
```

**If forgot user passwd, then:**
* run **Command-Prompt**<br>
`ubuntu config --default-user root`<br>
* run **Ubuntu**<br>
`passwd username`<br>
* **Command-Prompt**<br>
`ubuntu config --default-user username`<br>

---
### Xserver for Win11 display
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/MobaXterm_logo.png?raw=true)

* Download & Install [MobaXterm](https://mobaxterm.mobatek.net/download.html)
* Run MobaXterm to *find DISPLAY ip-address from X-server icon at upper-right corner*
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/MobaXterm_Xserver_listening_DISPLAYS.png?raw=true)

* set DISPLAY ip-address in ~/.bashrc<br>
`nano ~/.bashrc` # add 3 lines<br>
&ensp;export DISPLAY=**192.168.0.20:0**<br>
&ensp;export LIBGL_ALWAYS_INDIRECT=<br>
&ensp;export LIBGL_ALWAYS_SOFTWARE=1<br>

---
## ROS
[ROS Noetic for Ubuntu20.04](http://wiki.ros.org/noetic/Installation/Ubuntu)<br>

### ROS1 Installation
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt-get update
export ROS1_DISTRO=noetic # kinetic=16.04, melodic=18.04, noetic=20.04
sudo apt-get install ros-$ROS1_DISTRO-desktop-full
sudo apt-get install python3-catkin-tools python3-osrf-pycommon # ubuntu 20.04
sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev
```
**Environment setup**<br>
```
echo "alias source_ros1=\"source /opt/ros/$ROS1_DISTRO/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```

```
source_ros1
```

---
### [Tutorial: Understanding Nodes](http://wiki.ros.org/ROS/Tutorials/UnderstandingNodes)
`sudo apt-get install ros-noetic-turtlesim`<br>
**Open 6 Terminals to run the following:**<br>
1. ros master
```
source_ros1
roscore
```
2. list nodes & optics<br>
```
source_ros1
rosnode list
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/rosnode_list.png?raw=true)
`rosnode info /rosout`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/rosnode_info.png?raw=true)
`rostopic list`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/rostopic_list.png?raw=true)
3. turtlesim node
```
source_ros1
rosrun turtlesim turtlesim_node
```
![](http://wiki.ros.org/turtlesim?action=AttachFile&do=get&target=turtlesim.png)
4. Make the turtle move by arrow-keys
```
source_ros1
rosrun turtlesim turtle_teleop_key
```
5. print a publishing topic
```
source_ros1
rostopic echo /turtle1/cmd_vel
```
6. Make the turtle move in a circle (Ctrl-C to stop)
```
source_ros1
rostopic pub -r 1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]' 
```

---
### ROS USB-Cam
`sudo apt-get install ros-noetic-usb-cam`<br>

1. run master
```
source_ros1
roscore
```
2. launch usb_cam
```
source_ros1
roslaunch usb_cam usb_cam-test.launch
```
3. topic list
```
source_ros1
rostopic list
```
> /image_view/output<br>
> /image_view/parameter_descriptions<br>
> /image_view/parameter_updates<br>
> /rosout<br>
> /rosout_agg<br>
> /usb_cam/camera_info<br>
> /usb_cam/image_raw<br>
> /usb_cam/image_raw/compressed<br>
> /usb_cam/image_raw/compressed/parameter_descriptions<br>
> /usb_cam/image_raw/compressed/parameter_updates<br>
> /usb_cam/image_raw/compressedDepth<br>
> /usb_cam/image_raw/compressedDepth/parameter_descriptions<br>
> /usb_cam/image_raw/compressedDepth/parameter_updates<br>
> /usb_cam/image_raw/theora<br>
> /usb_cam/image_raw/theora/parameter_descriptions<br>
> /usb_cam/image_raw/theora/parameter_updates<br>

**NODES**:<br>
>  image_view (image_view/image_view)<br>
>  usb_cam (usb_cam/usb_cam_node)<br>

**PARAMETERS**<br>
* /image_view/autosize: True
* /rosdistro: noetic
* /rosversion: 1.15.14
* /usb_cam/camera_frame_id: usb_cam
* /usb_cam/image_height: 480
* /usb_cam/image_width: 640
* /usb_cam/io_method: mmap
* /usb_cam/pixel_format: yuyv
* /usb_cam/video_device: /dev/video0

---
## [ROS Tutorials](https://wiki.ros.org/ROS/Tutorials/)
### Navigating the ROS Filesystem
`sudo apt-get install ros-noetic-ros-tutorials`<br>

* rospack find [package_name]<br>
`rospack find roscpp`<br>

* roscd [package_name/subdir]<br>
`roscd roscpp`<br>

* ROS_PACKAGE_PATH<br>
`echo $ROS_PACKAGE_PATH`<br>
/opt/ros/noetic/share<br>

* rosls [package_name/subdir]<br>
`rosls roscpp_tutorials`<br>
 
---
### Creating Package: Beginner_Tutorials with talker & listener
```
source_ros1
mkdir -p ~/catkin_ws/src
```
* Initialize workspace
```
cd ~/catkin_ws
catkin init
```
* If you can not initialize workspace to ~/catkin_ws, then `rm -rf ~/.catkin_tools`<br>

* Create package
```
cd src
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp --rosdistro noetic
```

* Create talker.cpp & listener.cpp
```
cd beginner_tutorials/src
wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/roscpp_tutorials/talker/talker.cpp
wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/roscpp_tutorials/listener/listener.cpp
```

* Modify CMakeLists.txt for talker & listener
```
cd ..
mv CMakeLists.txt CMakeLists.txt.0
wget https://raw.github.com/ros/catkin_tutorials/master/create_package_pubsub/catkin_ws/src/beginner_tutorials/CMakeLists.txt
```

* Create messages & services
```
mkdir msg
echo "int64 num" > msg/Num.msg
mkdir srv
roscp rospy_tutorials AddTwoInts.srv srv/AddTwoInts.srv
```

* Using catkin_make to compile
```
cd ~/catkin_ws
catkin_make
```

* Using catkin build to compile
```
cd ~/catkin_ws
catkin build
```

**Exercise: Talker & Listener**<br>
1. ROS master
```
source_ros1 
roscore
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/roscore.png?raw=true)
2. Talker
```
source_ros1
cd ~/catkin_ws
source devel/setup.bash
rosrun beginner_tutorials talker
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/rosrun_beginner_tutorials_talker.png?raw=true)
3. Listener
```
source_ros1
cd ~/catkin_ws
source devel/setup.bash
rosrun beginner_tutorials listener
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/rosrun_beginner_tutorials_listener.png?raw=true)

---
## [Gym-Gazebo](https://github.com/erlerobot/gym-gazebo)
an extension of the initial OpenAI gym for robotics using ROS and Gazebo<br>

<table>
<tr>
<td>GazeboCircuit2TurtlebotLidar-v0</td>
<td>GazeboCircuitTurtlebotLidar-v0</td>
</tr>
<tr>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboCircuit2TurtlebotLidar-v0.png?raw=true"></td>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboCircuitTurtlebotLidar-v0.png?raw=true"></td>
</tr>
</table>

<table>
<tr>
<td>GazeboCartPole-v0</td>
<td>GazeboModularArticulatedArm4DOF-v1</td>
</tr>
<tr>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/cartpole.jpg?raw=true"></td>
<td><img width="70%" height="70%" src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularArticulatedArm4DOF-v1.jpg?raw=true"></td>
</tr>
</table>

<table>
<tr>
<td>GazeboModularScara4DOF-v3</td>
<td>GazeboModularScara3DOF-v3</td>
<td>GazeboModularScara3DOF-v2</td>
</tr>
<tr>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara4DOF-v3.png?raw=true"></td>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara3DOF-v3.png?raw=true"></td>
<td><img src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/GazeboModularScara3DOF-v2.png?raw=true"></td>
</tr>
</table>

ARIACPick-v0
<img width="75%" height="75%" src="https://github.com/erlerobot/gym-gazebo/blob/master/imgs/ariac_pick.jpg?raw=true">

---
### **[ROS Developement Studio (RDS)](https://www.theconstructsim.com/)**<br>
![](https://www.theconstructsim.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-10-at-17.08.49-1024x486.png)

**[exploring-ros-2-wheeled-robot-part-01](https://www.theconstructsim.com/exploring-ros-2-wheeled-robot-part-01/)**<br>
![](https://www.theconstructsim.com/wp-content/uploads/2019/04/m2wr_gazebo.png)

---
## ROS2
* [Installing ROS 2 on Ubuntu Linux](https://docs.ros.org/en/galactic/Installation/Ubuntu-Install-Binary.html)
* [Installing ROS 2 on macOS](https://docs.ros.org/en/galactic/Installation/macOS-Install-Binary.html)
* [Installing ROS 2 o Windows](https://docs.ros.org/en/galactic/Installation/Windows-Install-Binary.html)

### ROS2 install on Ubuntu20.04
**[Building ROS 2 on Ubuntu Linux](https://docs.ros.org/en/galactic/Installation/Ubuntu-Development-Setup.html)**<br>

```
sudo apt update && sudo apt install curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt-get update
export ROS2_DISTRO=galactic # dashing=18.04, galactic=20.04
sudo apt install ros-$ROS2_DISTRO-desktop
sudo apt-get install ros-$ROS2_DISTRO-ros2bag ros-$ROS2_DISTRO-rosbag2* # rosbag utilities (seems to be separate)
sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev
sudo apt-get install python3-pip
pip -V
pip install -U colcon-common-extensions
```
```
echo "alias source_ros2=\"source /opt/ros/$ROS2_DISTRO/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```
```
source_ros2
```

* test mutlicasting
```
ros2 multicast receive
```
```
ros2 multicast send
```
* If can not receive multicast, then run ufm as follows
```
sudo ufw allow in proto udp to 224.0.0.0/4
sudo ufw allow in proto udp from 224.0.0.0/4
```

---
### [Understanding ROS2 Nodes](https://docs.ros.org/en/galactic/Tutorials/Understanding-ROS2-Nodes.html)
![](https://docs.ros.org/en/galactic/_images/Nodes-TopicandService.gif)
`sudo apt-get install ros-galactic-turtlesim`<br>
**Open 3 Terminals to run the following:**<br>
1. turtlesim node
```
source_ros2
ros2 run turtlesim turtlesim_node
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtlesim_node.png?raw=true)
2. list nodes
```
source_ros2
ros2 node list
```
/turtlesim
3. turtlesim teleop-keyboard
```
source_ros2
ros2 run turtlesim turtle_teleop_key
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtle_teleop_key.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim.png?raw=true)
**Other operations:**<br>
* Remapping
```
ros2 run turtlesim turtlesim_node --ros-args --remap __node:=my_turtle
```
* ROS2 Node Info
```
ros2 node info /my_turtle
```

---
### ROS2 commands
* Demo in C++<br>
`ros2 run demo_nodes_cpp talker`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_demo_nodes_cpp-talker.png?raw=true)
`ros2 run demo_nodes_cpp listener`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_demo_nodes_cpp-listener.png?raw=true)

* Demo in Python<br>
`ros2 run demo_nodes_py talker`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_demo_nodes_py-talker.png?raw=true)
`ros2 run demo_nodes_py listener`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_demo_nodes_py-listener.png?raw=true)

* ROS2 Nodes:
  - `ros2 run turtlesim turtlesim_node`
  - `ros2 node list`
  - `ros2 node info /my_turtle`

* ROS2 Topics
  - `ros2 topic list`
  - `ros2 topic echo <topic_name>`
  - `ros2 topic info /turtle1/cmd_vel`
  - `ros2 topic pub <topic_name> <msg_type> '<args>'<br>`
  
* ROS2 Services
  - `ros2 service list`
  - `ros2 service type <service_name>`
  - `ros2 service list -t`
  - `ros2 service find <type_name>`
  - `ros2 interface show <type_name>.srv`
  - `ros2 service call <service_name> <service_type> <arguments>`

* ROS2 Parameters
  - `ros2 param list`
  - `ros2 param get <node_name> <parameter_name>`
  - `ros2 param set <node_name> <parameter_name> <value>`
  - `ros2 param dump <node_name>`
  - `ros2 param load <node_name> <parameter_file>`
  - `ros2 run <package_name> <executable_name> --ros-args --params-file <file_name>`
  
* ROS2 Actions
  - `ros2 action list`  
  - `ros2 action list -t`
  - `ros2 action info /turtle1/rotate_absolute`
  - `ros2 interface show turtlesim/action/RotateAbsolute`
  - `ros2 action send_goal <action_name> <action_type> <values>`
  
---
## micro-ROS
<img width="50%" height="50%" src="https://micro.ros.org/img/micro-ROS_big_logo.png">
micro-ROS puts ROS2 nodes onto microcontrollers

**[micro-ROS setup](https://github.com/micro-ROS/micro_ros_setup)**<br>
* [micro-ROS for Renesas e2 studio](https://github.com/micro-ROS/micro_ros_renesas2estudio_component)
* [micro-ROS component for ESP-IDF](https://github.com/micro-ROS/micro_ros_espidf_component)
* [micro-ROS module for Zephyr](https://github.com/micro-ROS/micro_ros_zephyr_module)
* [micro-ROS module for Mbed RTOS](https://github.com/micro-ROS/micro_ros_mbed)
* [micro-ROS app for Nuttx RTOS](https://github.com/micro-ROS/micro_ros_nuttx_app)
* [micro-ROS app for Microsoft Azure RTOS](https://github.com/micro-ROS/micro_ros_azure_rtos_app)
* [micro-ROS for STM32CubeMX/IDE](https://github.com/micro-ROS/micro_ros_stm32cubemx_utils)
* [micro-ROS for Arduino](https://github.com/micro-ROS/micro_ros_arduino)
* [micro-ROS module for Raspberry Pi Pico SDK](https://github.com/micro-ROS/micro_ros_raspberrypi_pico_sdk)

**ROS2 supported distributions are:**<br>
<table>
<tr><th>ROS 2 Distro</th><th>State</th><th>Branch</th></tr>
<tr><td>Crystal</td><td>EOL</td><td>`crystal`</td></tr>
<tr><td>Dashing</td><td>EOL</td><td>`dashing`</td></tr>
<tr><td>Foxy</td><td>Supported</td><td>`foxy`</td></tr>
<tr><td>Galactic</td><td>Supported</td><td>`galactic`</td></tr>
<tr><td>Rolling</td><td>Supported</td><td>`main`</td></tr>
</table>

---
### [eProsima Micro XRCE-DDS](https://github.com/eProsima/Micro-XRCE-DDS)
eProsima Micro XRCE-DDS is a library implementing the DDS-XRCE protocol as defined and maintained by the OMG, whose aim is to allow resource constrained devices such as microcontrollers
![](https://github.com/eProsima/Micro-XRCE-DDS/raw/master/docs/Concept.png?raw=true)
The Micro XRCE-DDS Clients request operations to the Agent to publish and/or subscribe to topics in the DDS global dataspace.
![](https://github.com/eProsima/Micro-XRCE-DDS-Agent/raw/master/docs/General.png?raw=true)

eProsima Micro XRCE-DDS contains:
* [Micro XRCE-DDS Client](https://github.com/eProsima/Micro-XRCE-DDS-Client)
* [Micro XRCE-DDS Agent](https://github.com/eProsima/Micro-XRCE-DDS-Agent)
* [Micro XRCE-DDS Gen](https://github.com/eProsima/Micro-XRCE-DDS-Gen)

---
### [Connect ESP32 to ROS2](https://medium.com/@SameerT009/connect-esp32-to-ros2-foxy-5f06e0cc64df)
1. ESP IDF Installation<br>
[ESP Get Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/)<br>

2. Source ROS2 setup<br>
```
cd ~/ros2_galactic
. ./install/local_setup.bash
cd ~
```
3. Micro-ROS Installation<br>
```
mkdir microros_ws
cd microros_ws
git clone -b galactic https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup
colcon build
source install/local_setup.bash
```

4. Creating a new firmware workspace for ESP32 <br>
`ros2 run micro_ros_setup create_firmware_ws.sh freertos esp32`<br>

5. Configuring created firmware<br>
`ros2 run micro_ros_setup configure_firmware.sh int32_publisher -t udp -i 192.168.1.7 -p 8888`<br>
`ros2 run micro_ros_setup build_firmware.sh menuconfig` # configure WiFi ssid & passwd<br>
Other [demo codes](https://github.com/micro-ROS/freertos_apps/tree/foxy/apps)<br>

6. Build firmware<br>
`ros2 run micro_ros_setup build_firmware.sh`<br>

7. Flash firmware<br>
`ros2 run micro_ros_setup flash_firmware.sh`<br>

8. Create the micro-ROS agent<br>
`ros2 run micro_ros_setup create_agent_ws.sh`<br>
`ros2 run micro_ros_setup build_agent.sh`<br>
`source install/local_setup.bash`<br>

9. Running the micro-ROS agent<br>
`ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888`<br>
Once connected: <br>
![](https://miro.medium.com/max/2000/1*Gp97hV_qzgiUbcbaQwepGQ.png)

10. Testing the micro-ROS app<br>
`ros2 topic list`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_topic_list.png?raw=true)
`ros2 topic echo /freertos_int32_publisher`<br>

11. ESP32 running micro-ROS client<br>
`ros2 topic echo /microros_esp32`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_topic_echo_microros_esp32.png?raw=true)

---
### [micro-ROS for Arduino](https://github.com/micro-ROS/micro_ros_arduino)
For ESP32, use [ESP32 Arduino v2.0.2](https://github.com/espressif/arduino-esp32/releases/tag/2.0.2)<br>

* Preference URLs: https://github.com/espressif/arduino-esp32/releases/download/2.0.2/package_esp32_index.json
* Download [the latest micro-ROS library for Arduino](https://github.com/micro-ROS/micro_ros_arduino) / [release](https://github.com/micro-ROS/micro_ros_arduino/releases)<br>
* Sketch>Include Library>Add .ZIP Library>  **micro_ros_arduino-galactic.zip**
* Sketchbook>[ESP32_microros_publisher_wifi](https://github.com/rkuo2000/arduino/blob/master/examples/ESP32_microros_publisher_wifi/ESP32_microros_publisher_wifi.ino)

---
### ROS2 on ESP32
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

