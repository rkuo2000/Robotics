---
layout: post
title: 嵌入式開發板 - Raspberry
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

介紹樹莓派嵌入式開發板, 包括開發板規格, 安裝Ubuntu server 22.04 LTS作業系統, 安裝ROS/ROS2 機器人作業系統, 以及
安裝Pi-Camera與YDLiDAR x4驅動程式, 以便進行影像處理, 物件偵測, 跟強化學習.

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
### Socket pinout
![](https://dsalearning.github.io/assets/images/raspberrypi/raspberry-pi-GPIO-Header-with-Photo-702x336.png)

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
1. check the current kernel version
`uname -r `<br>
2. download the Bash script to change the kernel
`wget https://raw.githubusercontent.com/pimlie/ubuntu-mainline-kernel.sh/master/ubuntu-mainline-kernel.sh`<br>
`chmod +x ubuntu-mainline-kernel.sh`<br>
`sudo mv ubuntu-mainline-kernel.sh /usr/local/bin/`<br>
3. check available kernel versions to install
`ubuntu-mainline-kernel.sh -c`<br>
`ubuntu-mainline-kernel.sh -r`<br>
4. Change or upgrade default Ubuntu 22.04 | 20.04 Kernel version
`sudo ubuntu-mainline-kernel.sh -i`<br>

`sudo ubuntu-mainline-kernel.sh -i version-number`<br>
5. 
`sudo ubuntu-mainline-kernel.sh -l`<br>

6. Reboot
`sudo reboot`<br>
`uname -r `<br>
7. Change or Set Default Kernel Version
`sudo nano /etc/default/grub`<br>
`GRUB_SAVEDEFAULT=true`
`GRUB_DEFAULT=saved`

---
## 安裝機器人作業系統

### ROS install on Ubuntu 22.04 LTS

---
### ROS2 install on Ubuntu22.04 LTS
<img width="25" height="20%" src="https://www.ros.org/imgs/humble.png">

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

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

