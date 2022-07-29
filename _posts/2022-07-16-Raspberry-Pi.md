---
layout: post
title: 嵌入式開發板 - Raspberry
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

介紹樹莓派嵌入式開發板, 安裝Ubuntu作業系統, 安裝ROS機器人作業系統, 以及
Pi-Camera與LiDAR驅動程式安裝, 以便進行影像處理, 物件偵測, 跟強化學習.

---
## 樹莓派開發板(Raspberry Pi)

### RPi4
![](https://www.taiwansensor.com.tw/wp-content/uploads/2020/04/RPI-006544-7-600x366.jpg)
Specification:
* Processor：
  - Broadcom **BCM2711** 
  - quad-core Cortex-A72 (ARM v8)   
  - 64-bit SoC @ **1.5GHz**
* Memory： 1GB / 2GB / 4GB LPDDR4   (depending on model)
* Connectivity：
  - 2.4 GHz and 5.0 GHz IEEE 802.11b/g/n/ac wireless LAN,   
  - Bluetooth 5.0, BLE Gigabit Ethernet   
  - 2 × USB 3.0 ports   
  - 2 × USB 2.0 ports.
* GPIO：Standard 40-pin GPIO header (fully backwards-compatible with previous boards)
* Video & Sound： 
  - 2 × **micro HDMI** ports (up to **4Kp60** supported)   
  - 2-lane MIPI **DSI** display port     
  - 2-lane MIPI **CSI** camera port   
  - 4-pole stereo audio and composite video port
* Multimedia：
  - H.265 (4Kp60 decode);   
  - H.264 (1080p60 decode, 1080p30 encode);   
  - OpenGL ES 3.0 graphics
* SD card support： 
  - Micro SD card slot for loading operating system and data storage
* Input power：
  - 5V DC via USB-C connector (minimum 3A1)   
  - 5V DC via GPIO header (minimum 3A1)   
  - Power over Ethernet (PoE)–enabled (requires separate PoE HAT)
* **5V 3A** Power Input

---
### RPi3B+
![](https://a.rimg.com.tw/s9/436/95b/rhyu005/5/2e/22210173970734_201.jpg)
Specification:
* Processor：
  - Broadcom **BCM2837B0** 
  - quad-core Cortex-A53 (ARM v8)   
  - 64-bit SoC @ **1.4GHz**
* Memory： 1GB LPDDR3   
* Connectivity：
  - 2.4 GHz and 5.0 GHz IEEE 802.11b/g/n/ac wireless LAN   
  - Bluetooth 4.2, BLE, Gigabit Ethernet   
  - 4 × USB 2.0 ports
* GPIO：Standard 40-pin GPIO header
* Video & Sound： 
  - 1 × **fullsize HDMI** ports (up to FullHD 1920*1080)
  - 1-lane MIPI **DSI** display port     
  - 1-lane MIPI **CSI** camera port   
  - 4-pole stereo audio and composite video port
* Multimedia：  - 
  - H.264,MPEG-4 (1080p30) decode, H.264 1080p30 encode
  - composite video port
  - OpenGL ES 1.1,2.0 graphics
* SD card support： 
  - Micro SD card slot for loading operating system and data storage
* Input power：
  - 5V/2.5A DC via micro USB connector
  - 5V DC via GPIO header
  - Power over Ethernet (PoE)-enabled (required seperate PoE HAT)
* Environment: Operating temperature 0~50°C

---
### RPi3B
![](https://www.jameco.com/jameco/workshop/circuitnotes/raspberry_pi_circuit_note_fig2.jpg)
Specification: same as RPi3B+ except **1.2GHz** BCM2837

---
## 安裝Ubuntu 22.04 LTS作業系統 (real-time版本)
**[Install Ubuntu on a Raspberry Pi](https://ubuntu.com/download/raspberry-pi)**<br>
Download [Ubuntu Server 22.04 LTS 64-bit](https://ubuntu.com/download/raspberry-pi/thank-you?version=22.04&architecture=server-arm64+raspi)<br>

### Ubuntu server 22.04 LTS 64-bit
[Install Ubuntu Core on a Raspberry Pi](https://ubuntu.com/download/raspberry-pi-core)
1. What you need:　 
* A microSD card (4GB minimum, 8GB recommended)
* A computer with a microSD card drive
* A Raspberry Pi 2, 3 or 4
* A micro-USB power cable (USB-C for the Pi 4)
* A Wi-Fi network or an ethernet cable with an internet connection

2. Prepare the SD card
* Download .img.xz & uncompress it to .img
* To write .img into SDcard, you can use **Win32DiskImager** or **balenaEtcher**

3. plugin SDcard and power up RPi3/4

4. default username: `ubuntu`, password: `ubuntu`

* To fit TV screen
`sudo nano /boot/firmware/config.txt`<br>
```
#disable_overscan = 1
```

* To set a WiFi connection
`sudo nano /boot/firmware/network-config`<br>
```
network:
  version 2:
  renderer: networkd
  ethernets:
    eth0:
	  dhcp4: true
	  optional: true
  wifis:
    wlan0:
      dhcp4: true
      optional: true
      access-points:
        "CBN-42738-=2.4G":
          password: "0972211921"
```
`sudo netplan generate`<br>
`sudo netplan apply`<br>

`sudo apt update`<br>
`sudo apt install wpasupplicant`<br>

---
### 更新Linux核心版本
[How to change default kernel in Ubuntu 22.04 | 20.04 LTS](https://www.how2shout.com/linux/how-to-change-default-kernel-in-ubuntu-22-04-20-04-lts/)<br>

1. check the current kernel version<br>
`uname -r `<br>
2. download the Bash script to change the kernel<br>
```
wget https://raw.githubusercontent.com/pimlie/ubuntu-mainline-kernel.sh/master/ubuntu-mainline-kernel.sh
chmod +x ubuntu-mainline-kernel.sh
sudo mv ubuntu-mainline-kernel.sh /usr/local/bin/
```
3. check available kernel versions to install<br>
`ubuntu-mainline-kernel.sh -c`<br>
4. install the latest available version of Ubuntu 22.04 Kernel<br>
`sudo ubuntu-mainline-kernel.sh -i`<br>
5. list what are the available versions of Kernel on our system:<br>
`sudo ubuntu-mainline-kernel.sh -l`<br>
5. Reboot your system<br>
`sudo reboot`<br>
`uname -r `<br>
6. Change the Default Kernel Version<br>
`sudo nano /etc/default/grub`<br>
```
GRUB_SAVEDEFAULT=true
GRUB_DEFAULT=saved
```
`sudo update-grub`<br>
7. reboot your system<br>
![](https://www.how2shout.com/linux/wp-content/uploads/2022/01/Advanced-options-for-Ubuntu.jpg)
![](https://www.how2shout.com/linux/wp-content/uploads/2022/01/Select-the-Default-kernel-you-want-to-use.png)
8. uninstall or remove<br>
`sudo ubuntu-mainline-kernel.sh -u`<br>
![](https://www.how2shout.com/linux/wp-content/uploads/2022/01/Uninstall-the-installed-kernel-version-on-Ubuntu-22.04.png)

---
## 安裝機器人作業系統

### ROS2 install on Ubuntu22.04 LTS
<img width="25%" height="20%" src="https://www.ros.org/imgs/humble.png">

Ubuntu 22.04 LTS install ROS2
(https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html#)

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

# ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.
sudo apt install ros-humble-ros-base
```

```
echo "alias source_ros2=\"source /opt/ros/humble/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```

**ROS2 test run**<br>
`source /opt/ros/humble/setup.bash`<br>

1. test Talker-Listern
* On one terminal
```
source_ros2
ros2 run demo_nodes_cpp talker
```
* In another terminal
```
source_ros2
ros2 run demo_nodes_py listener
```

2. test multicasting
```
source_ros2
ros2 multicast receive
```
<br>
```
source_ros2
ros2 multicast send
```
* If can not receive multicast, then run ufm as follows
```
sudo ufw allow in proto udp to 224.0.0.0/4
sudo ufw allow in proto udp from 224.0.0.0/4
```

3. test Turtlesim
* turtlesim node
```
source_ros2
ros2 run turtlesim turtlesim_node
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtlesim_node.png?raw=true)


* turtlesim teleop-keyboard
```
source_ros2
ros2 run turtlesim turtle_teleop_key
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtle_teleop_key.png?raw=true)
* topic echo
```
source_ros2
ros2 node list
```
/turtlesim

``` 
ros2 topic echo /turtle1/cmd_vel
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim.png?raw=true)

---
### [v4l2_camera](https://index.ros.org/r/v4l2_camera/)
A ROS 2 camera driver using Video4Linux2 (V4L2)<br>
* Install ROS package
`sudo apt-get install ros-humble-v4l2-camera`<br>

* Build from source
`git clone --branch foxy https://gitlab.com/boldhearts/ros2_v4l2_camera.git src/v4l2_camera`<br>
`colcon build`<br>

* Usage:
`ros2 run v4l2_camera v4l2_camera_node`<br>

`ros2 run rqt_image_view rqt_image_view`<br>

* Dependencies
**image_transport** - makes it possible to set up compressed transport of the images, as described below.<br>
The ROS 2 port of image_transport in the image_common repository is needed inside of your workspace:<br>
`git clone --branch ros2 https://github.com/ros-perception/image_common.git src/image_common`<br>

* Nodes: v4l2_camera_node
Published Topics:<br>
/raw_image - sensor_msgs/Image<br>
    
<iframe width="893" height="558" src="https://www.youtube.com/embed/vgGuKtmOW4Q" title="Ros2 + Raspberry + Camera #Ros2 #Camera #Raspberry #Foxy" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## OpenCV Image Processing

### Install OpenCV
* Install OpenCV on Ubuntu 22.04 (Python3.10.4)<br>
`pip3 install opencv-python`<br>

* Install OpenCV on Windows 11 
  - Install [Python for Windows](https://www.python.org/downloads/)
  - Install [Git for Windows](https://gitforwindows.org/)
  - Run Gitbash to install opencv-python<br>
    `pip3 install opencv-python`<br>

---
### Object Detection with Color
[Detect Objects of Similar Color using OpenCV in Python](https://techvidvan.com/tutorials/detect-objects-of-similar-color-using-opencv-in-python/)<br>
![](https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2021/06/draw-contour.png)

[Object Detection and Tracking with OpenCV and Python](https://www.bluetin.io/opencv/object-detection-tracking-opencv-python/)<br>
![](https://www.bluetin.io/wp-content/uploads/2017/12/opencv-bounding-rectangle-example.jpg)

[cam_object_tracking.py](https://github.com/rkuo2000/cv2/blob/master/cam_object_tracking.py)<br>

---
### Optical Flow
**Blog:** [Introduction to Motion Estimation with Optical Flow](https://nanonets.com/blog/optical-flow/)<br>
![](https://nanonets.com/blog/content/images/2019/04/sparse-vs-dense.gif)

**Code:** [rkuo2000/cv2](https://github.com/rkuo2000/cv2)<br>
* [optical-flow-sparse.py](https://github.com/rkuo2000/cv2/blob/master/optical-flow-sparse.py)
* [optical-flow-dense.py](https://github.com/rkuo2000/cv2/blob/master/optical-flow-dense.py)

**Usage:**<br>
```
cd ~
git clone https://github.com/rkuo2000/cv2
cd cv2
python3 optical-flow-sparse.py
```

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

