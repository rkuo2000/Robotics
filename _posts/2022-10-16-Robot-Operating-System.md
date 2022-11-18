---
layout: post
title: ROS - Robot Operating System
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications.

---
## ROS簡介
[ROS簡介及教學資源整理](https://ithelp.ithome.com.tw/articles/10200551)<br>
他其實是安裝在Linux的環境上面.([Linux系統—架構淺析](https://iter01.com/488176.html))<br>
ROS比較像是在負責為機器人的各個元件進行溝通與操作的一個框架，
以機器人的行走為例，要讓機器人走路需要控制其底下的馬達、還有一些感測器以進行避障等等，
ROS內就有這種類型的函式可以讓控制馬達的程式得以與接收感測器的程式溝通，如下圖所示:
![](https://ithelp.ithome.com.tw/upload/images/20181016/20112348nhibAqMhTR.png)

---
### ROS-based communication architecture
**Paper:** [A ROS2 based communication architecture for control in collaborative and intelligent automation systems](https://arxiv.org/abs/1905.09654)<br>

**ROS** is a collection of tools and libraries that aids robotics software development. Software is written in form of nodes that exchange messages using a transport layer called **TCPROS** based on standard TCP/IP sockets.

**ROS** has a centralized network configuration which means that there has to exist a running ROS master. 
To improve on this design limitation, developers of **ROS2** implemented Object Management Group’s standard **DDS** as the communication middleware considering it to be scalable, robust and well-proven in mission-critical systems.

![](https://images.deepai.org/converted-papers/1903.05850/figures/station.jpg)
An Automated Guided Vehicle (AGV) carrying a diesel truck engine and an autonomous mobile platform (MiR100) carrying kitted material to be assembled on an engine enter the Collaborative Robot Assembly Station.
<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/ROS2%20high-level%20communication%20overview.png?raw=true)
<br>

---
### [Robots using ROS](http://library.isr.ist.utl.pt/docs/roswiki/Robots.html)
![](https://github.com/rkuo2000/Robotics/blob/main/images/Robots_using_ROS.png?raw=true)

---
### TurtleBot
![](https://github.com/rkuo2000/Robotics/blob/main/images/ROS%20Robot%20System%20Diagram.png?raw=true)
[TurtleBot3 手冊](https://github.com/ROBOTIS-GIT/turtlebot3)<br>
![](https://emanual.robotis.com/assets/images/platform/turtlebot3/overview/turtlebot3_with_logo.png)

---
## [ROS](https://www.ros.org/) distro
[List of Distributions](https://docs.ros.org/en/rolling/Releases.html)<br>

* ROS **Noetic Ninjemys** on Ubuntu 20.04 (Recommended for Latest ROS 1 LTS) [Install](http://wiki.ros.org/noetic/Installation/Ubuntu)

* ROS **Foxy Fitzroy** on Ubuntu 20.04, macOS (10.14), or Windows (VS2019) (Recommended for Latest ROS 2 LTS) [Install](https://docs.ros.org/en/foxy/Installation.html)

* ROS **Humble Hawksbill** on Ubuntu 22.04, macOS, or Windows (VS2019) (Recommended for Latest ROS 2) [Install](https://docs.ros.org/en/humble/Installation.html)


<table>
<tr>
<td><b>Noetic Ninjemys</b></td>
<td><b>Foxy Fitzroy</b></td>
<td><b>Humble Hawksbill</b></td>
</tr>
<tr>
<td><img width="25%" height="25%" src="https://www.ros.org/imgs/ros-noetic-ninjemys.svg"></td>
<td><img src="https://docs.ros.org/en/foxy/_static/foxy-small.png"></td>
<td><img src="https://docs.ros.org/en/humble/_static/humble-small.png"></td>
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

---
## Ubuntu22.04 on Windows 11
[在Windows 10 使用WSL2 安裝Linux系統](https://rdfarm.net/windows-10-install-wsl2/)<br>
[WSL 的基本命令](https://docs.microsoft.com/zh-tw/windows/wsl/basic-commands)<br>

### 啟用 Windows子系統Linux 與 虛擬機器平台
* Open **PowerShell** as administrator (管理者權限)<br>
* 啟用 Windows 子系統 Linux
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
* 啟用 虛擬機器平台 
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
* 更新wsl
```
wsl --status
wsl --update
```
* 設WSL2為預設版本
```
wsl --set-default--version 2
wsl -l -v
```

### 安裝Microsoft商店的 Ubuntu 22.04 LTS
![](https://github.com/rkuo2000/Robotics/blob/main/images/ubuntu22.04.1_LTS_for_Win11.png?raw=true)

### export Ubuntu for backup
* Open PowerShell as adminstrator
```
wsl --shutdown
wsl -l -v
cd D:\WSL\Backup
wsl --export Ubuntu-22.04 ubuntu_backup.tar
```

---
### How to move existing WSL installation to D: drive
<iframe width="989" height="556" src="https://www.youtube.com/embed/ON_dPAO4KZs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
move C:\Users\username\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4
to D:\WSL\Working


---
### Reset User Password if forgotten
* run **Command-Prompt**<br>
`ubuntu config --default-user root`<br>
* run **Ubuntu**<br>
`passwd user_name`<br>
* **Command-Prompt**<br>
`ubuntu config --default-user user_name`<br>

---
### Xserver for Win11 display
![](https://github.com/rkuo2000/Robotics/blob/main/images/MobaXterm_logo.png?raw=true)

* Download & Install [MobaXterm](https://mobaxterm.mobatek.net/download.html)
* Run MobaXterm to *find DISPLAY ip-address from X-server icon at upper-right corner*
![](https://github.com/rkuo2000/Robotics/blob/main/images/MobaXterm_Xserver_listening_DISPLAYS.png?raw=true)

* set DISPLAY ip-address in ~/.bashrc<br>
`nano ~/.bashrc` # add 3 lines below<br>
&ensp;export DISPLAY=**192.168.0.20:0**<br>
&ensp;export LIBGL_ALWAYS_INDIRECT=<br>
&ensp;export LIBGL_ALWAYS_SOFTWARE=1<br>

---
### Ubuntu22.04 on RPi4
![](https://res.cloudinary.com/canonical/image/fetch/f_auto,q_auto,fl_sanitize,c_fill,w_720/https://ubuntu.com/wp-content/uploads/a9c1/Screenshot-from-2022-04-18-13-05-17-min.png)
* **[How to install Ubuntu 22.04 LTS on Raspberry Pi 4](https://linuxhint.com/install-ubuntu-22-04-lts-raspberry-pi/)**
* [Performance Tips for Ubuntu 22.04 on Raspberry Pi 4](https://teejeetech.com/2022/06/04/tweaks-for-ubuntu-22-04-on-raspberry-pi-4/)

---
## ROS
[ROS Noetic for Ubuntu20.04](http://wiki.ros.org/noetic/Installation/Ubuntu)<br>
(kinetic=16.04, melodic=18.04, noetic=20.04)<br>

### [Ubuntu install of ROS Noetic](http://wiki.ros.org/noetic/Installation/Ubuntu)
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
![](https://github.com/rkuo2000/Robotics/blob/main/images/rosnode_list.png?raw=true)
`rosnode info /rosout`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/rosnode_info.png?raw=true)
`rostopic list`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/rostopic_list.png?raw=true)
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
![](https://github.com/rkuo2000/Robotics/blob/main/images/roscore.png?raw=true)
2. Talker
```
source_ros1
cd ~/catkin_ws
source devel/setup.bash
rosrun beginner_tutorials talker
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/rosrun_beginner_tutorials_talker.png?raw=true)
3. Listener
```
source_ros1
cd ~/catkin_ws
source devel/setup.bash
rosrun beginner_tutorials listener
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/rosrun_beginner_tutorials_listener.png?raw=true)

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

### [install ROS2 on ubuntu20.04 LTS](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html#)
![](https://docs.ros.org/en/foxy/_static/foxy-small.png)

### [install ROS2 on Ubuntu22.04 LTS](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html#)
![](https://docs.ros.org/en/humble/_static/humble-small.png)
 
```
sudo apt install software-properties-common
sudo add-apt-repository universe

sudo apt update && sudo apt install curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update
sudo apt upgrade

# Desktop Install (Recommended): ROS, RViz, demos, tutorials.
sudo apt install ros-humble-desktop
```

```
echo "alias source_ros2=\"source /opt/ros/humble/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```

---
### To uninstall it
```
sudo apt remove ~nros-humble-* && sudo apt autoremove
```
you may also want to remove the repository:<br>
```
sudo rm /etc/apt/sources.list.d/ros2.list
sudo apt update
sudo apt autoremove
# Consider upgrading for packages previously shadowed.
sudo apt upgrade
```

* [ROS2 Tutorials](https://docs.ros.org/en/humble/Tutorials.html)<br>

---
### Try examples
`source /opt/ros/humble/setup.bash`<br>

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

* Talker-Listener 
  - On one terminal
```
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp talker
```
  - In another terminal
```
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_py listener
```

---
### [Understanding ROS2 Nodes](https://docs.ros.org/en/galactic/Tutorials/Understanding-ROS2-Nodes.html)
![](https://docs.ros.org/en/galactic/_images/Nodes-TopicandService.gif)
`sudo apt-get install ros-galactic-turtlesim` (for Ubuntu20.04 LTS)<br>
`sudo apt-get install ros-humble-turtlesim`   (for Ubuntu22.04 LTS)<br>

**Open 3 Terminals to run the following:**<br>
1. turtlesim node
```
source_ros2
ros2 run turtlesim turtlesim_node
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim_turtlesim_node.png?raw=true)
2. list nodes
```d
source_ros2
ros2 node list
```
/turtlesim
3. turtlesim teleop-keyboard
```
source_ros2
ros2 run turtlesim turtle_teleop_key
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim_turtle_teleop_key.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim.png?raw=true)

4. topic echo
``` 
ros2 topic echo /turtle1/cmd_vel
```

**Other operations:**<br>
* Remapping
```
ros2 run turtlesim turtlesim_node --ros-args --remap __node:=my_turtle
```
* ROS2 Node Info
```
ros2 node info /turtlesim
```

---
### ROS2 commands
* Demo in C++<br>
`ros2 run demo_nodes_cpp talker`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_demo_nodes_cpp-talker.png?raw=true)
`ros2 run demo_nodes_cpp listener`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_demo_nodes_cpp-listener.png?raw=true)

* Demo in Python<br>
`ros2 run demo_nodes_py talker`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_demo_nodes_py-talker.png?raw=true)
`ros2 run demo_nodes_py listener`<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_demo_nodes_py-listener.png?raw=true)

* ROS2 Nodes:
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
 
<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

