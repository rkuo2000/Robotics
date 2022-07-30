---
layout: post
title: 嵌入式開發板 - Raspberry
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

介紹嵌入式開發板 樹莓派RPi4B,及使用 Ubuntu Desktop 22.04 LTS 作業系統(Real-Time), OpenCV-Python 影像處理, Pi-Camera與IMU 驅動程式, ROS2機器人作業系統 (達成實時飛控板通訊).

---
## 樹莓派開發板(Raspberry Pi)

### RPi4B
![](https://www.taiwansensor.com.tw/wp-content/uploads/2020/04/RPI-006544-7-600x366.jpg)
[RPi4B Specification](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/specifications/):<br>
* Processor：
  - Broadcom **BCM2711** 
  - quad-core Cortex-A72 (ARM v8)   
  - 64-bit SoC @ **1.5GHz**
* Memory： 4GB LPDDR4-3200
* Connectivity：
  - 2.4 GHz and 5.0 GHz IEEE 802.11ac wireless, Bluetooth 5.0, BLE   
  - Gigabit Ethernet   
  - 2 USB 3.0 ports; 2 USB 2.0 ports  
* GPIO：Raspberry Pi Standard 40-pin GPIO header (fully backwards-compatible with previous boards)
* Video & Sound： 
  - 2 × **micro HDMI** ports (up to **4Kp60** supported)   
  - 2-lane MIPI **DSI** display port     
  - 2-lane MIPI **CSI** camera port   
  - 4-pole stereo audio and composite video port
* Multimedia：
  - H.265 (4kp60 decode), H264 (1080p60 decode, 1080p30 encode)
  - OpenGL ES 3.1, Vulkan 1.0
* SD card support： 
  - Micro SD card slot for loading operating system and data storage
* Input power：
  - 5V DC via USB-C connector (minimum 3A)   
  - 5V DC via GPIO header (minimum 3A)   
  - Power over Ethernet (PoE)–enabled (requires separate PoE HAT)
  - A good quality 2.5A power supply can be used if downstream USB peripherals consume less than 500mA in total.
* Operating temperature: 0 – 50 degrees C ambient

---
### Raspberry Pi standard GPIO header
![](https://www.raspberrypi-spy.co.uk/wp-content/uploads/2012/06/Raspberry-Pi-GPIO-Header-with-Photo-768x512.png)

---
## Ubuntu 22.04 LTS 作業系統 (Real-Time OS)

### [Install Ubuntu on a Raspberry Pi](https://ubuntu.com/download/raspberry-pi)**<br> 
Based on upstream v5.15, the 22.04 LTS kernel integrates the out-of-tree PREEMPT_RT patch for x86_64 and AArch64 architectures.<br>
* Download [Ubuntu Desktop 22.04 LTS 64-bit](https://ubuntu.com/download/raspberry-pi/thank-you?version=22.04&architecture=desktop-arm64+raspi)<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/RPi4_Ubuntu2204_Desktop.png?raw=true)

---
### [Install Ubuntu Core on a Raspberry Pi](https://ubuntu.com/download/raspberry-pi-core)
1. get a SD card = 16GB

2. Download .img.xz & uncompress it to .img
   To write .img into SDcard, you can use **Win32DiskImager** or **balenaEtcher**

3. plugin SDcard and power up RPi3/4

4. default username: `ubuntu`, password: `ubuntu`

* To fit TV screen
`sudo nano /boot/firmware/config.txt`<br>
```
#disable_overscan = 1
```

---
## OpenCV Image Processing

### Python3
`python3 -V`<br>
* 安裝 pip3
`sudo apt-get install python3-pip`<br>
* 更新 pip3
`pip3 install --upgrade pip`<br>

---
### Install OpenCV
* Install OpenCV on **Ubuntu 22.04** (Python3.10.4)<br>
`pip3 install opencv-python`<br>

* Install OpenCV on **Windows 11**
  - Install [Python for Windows](https://www.python.org/downloads/)
  - Install [Git for Windows](https://gitforwindows.org/)
  - Run Gitbash to install opencv-python<br>
    `pip3 install opencv-python`<br>

* Download [OpenCV 程式範例 ](https://github.com/rkuo2000/cv2)
```
cd ~
git clone https://github.com/rkuo2000/cv2
cd ~/cv2
```

* 使用鏡頭
1. USB camera
```
ls -l /dev/video0
cd ~/cv2
python3 cam.py
```
2. Pi-camera (to CSI connector)
```
cd ~/cv2
python3 picam.py
```

---
### Object Detection using Color
[Detect Objects of Similar Color using OpenCV in Python](https://techvidvan.com/tutorials/detect-objects-of-similar-color-using-opencv-in-python/)<br>
![](https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2021/06/draw-contour.png)

[Object Detection and Tracking with OpenCV and Python](https://www.bluetin.io/opencv/object-detection-tracking-opencv-python/)<br>
![](https://www.bluetin.io/wp-content/uploads/2017/12/opencv-bounding-rectangle-example.jpg)

---
[cam_object_tracking.py](https://github.com/rkuo2000/cv2/blob/master/cam_object_tracking.py)<br>
* Usage:
```
cd ~/cv2
python3 cam_object_tracking.py 
```

* Change Color range
1. use PaintBrush(小畫家) to find color range in **HSV** (挑兩個點找出綠色的範圍)
<table>
  <tr>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PaintBrush_HSV_Green1.png?raw=true"></td>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PaintBrush_HSV_Green2.png?raw=true"></td>
  </tr>
</table>
2. edit .py to adjust the color range
  - Blue color
```
lower_blue = np.array([110,50,50])
upper_blue = np.array([130,255,255])
```
  - Green color
```
lower_blue = np.array([75,55,0])
upper_blue = np.array([153,98,0])
```

---
### Optical Flow (光流)
**Blog:** [Introduction to Motion Estimation with Optical Flow](https://nanonets.com/blog/optical-flow/)<br>
![](https://nanonets.com/blog/content/images/2019/04/sparse-vs-dense.gif)

**Blog:** [OpenCV Optical Flow介紹](https://meetonfriday.com/posts/e2795e5a/)<br>
* 了解Optical Flow的概念，以及如何使用Lucas-Kanade method來計算它
* 使用cv.calcOpticalFlowPyrLK()來追蹤影片的特徵點
* 使用cv.calcOpticalFlowFarneback()來計算稠密光流

**Code:** [rkuo2000/cv2](https://github.com/rkuo2000/cv2)<br>
* [optical-flow-sparse.py](https://github.com/rkuo2000/cv2/blob/master/optical-flow-sparse.py) 顯示原影像與特徵點的光跡
* [optical-flow-dense.py](https://github.com/rkuo2000/cv2/blob/master/optical-flow-dense.py) 顯示原影像與稠密度的光跡
* [drone_optical_flow.py](https://github.com/rkuo2000/cv2/blob/master/drone_optical_flow.py) 只顯示特徵點的光跡

**Usage:**<br>
```
cd ~
git clone https://github.com/rkuo2000/cv2
cd cv2
python3 optical-flow-sparse.py
python3 drone_optical_flow.py
```

---
## MAVlink

### [Communicating with Raspberry Pi via MAVLink](https://ardupilot.org/dev/docs/raspberry-pi-via-mavlink.html)
Connect the flight controller’s **TELEM2** port to the RPi’s **TXD0**(GPIO14), **RXD0**(GPIO) and **Ground**  pins.

**Setting up the flight controller**<br>
Connect to the flight controller with a ground station (i.e. Mission Planner) and set the following parameters:<br>
* **SERIAL2_PROTOCOL** = 2 (the default) to enable MAVLink 2 on the serial port.
* **SERIAL2_BAUD** = 921 so the flight controller can communicate with the RPi at 921600 baud.
*　**LOG_BACKEND_TYPE** = 3 if you are using APSync to stream the dataflash log files to the RPi

### MAVProxy
MAVProxy can be used to send commands to the flight controller from the Pi. It can also be used to route telemetry to other network endpoints.
This assumes you have a SSH connection to the Pi.<br>
```
sudo apt-get install python3-dev python3-opencv python3-wxgtk4.0 python3-pip python3-matplotlib python3-lxml python3-pygame
pip3 install PyYAML mavproxy --user
echo "export PATH=$PATH:$HOME/.local/bin" >> ~/.bashrc
```

### Over USB
`pip3 install mavproxy pymavlink --user --upgrade`<br>
* For Linux:<br>
`mavproxy.py --master=/dev/ttyUSB0`<br>
* For Windows:<br> 
`mavproxy --master=COM14`<br>
* For MacOS:<br>
`mavproxy.py --master=/dev/ttyusbserialxxx`<br>

### Over Network
```
mavproxy.py --master=tcp:192.168.1.1:14550
mavproxy.py --master=udp:127.0.0.1:14550
mavproxy.py --master=tcp:0.0.0.0:14550
```
If connecting to a remote IP address,<br>
```
mavproxy.py --master=udpout:10.10.1.1:14550
mavproxy.py --master=tcpout:10.10.1.1:14550
```

### Startup Options
```
mavproxy.py --master=/dev/ttyUSB0 --out=udp:192.168.1.1:14550
mavproxy.py --master=/dev/ttyACM0,115200 --out=/dev/ttyUSB0,57600
mavproxy.py --master=/dev/ttyACM0,115200 --out=COM17,57600
mavproxy.py --master=/dev/ttyACM0,57600 --out=udpbcast:192.168.2.255:14550
```

### Telemtry Forwarding
![](https://ardupilot.org/mavproxy/_images/Mavproxy_usage.jpg)

### Local Forwarding
```
mavproxy.py --master=/dev/ttyACM0 --baudrate 115200 --out 127.0.0.1:14550
mavproxy.py --out 127.0.0.1:14550
```

* For Windows PC, start a command prompt and enter
`mavproxy --master=COMx --out 127.0.0.1:14550`<br>

### Startup Scripts

[Settings](https://ardupilot.org/mavproxy/docs/getting_started/settings.html)<br>

### Examples (Aircraft's name is "Quaddy")
`mavproxy.py --baud=57600 --aircraft="Quaddy" --speech --console --map --quadcopter`<br>
`mavproxy.py --master=COM17,9600 --out=udpin:0.0.0.0:14550 --daemon`<br>
`mavproxy.py --master=\dev\ttyUSB0,57600 --master=udpin:192.168.16.15:2626`<br>

### Multiple Vehicles with MAVProxy
![](https://ardupilot.org/mavproxy/_images/multi_veh.png)
* Use alllinks <cmd> to send <cmd> to all vehicles in turn. For example, alllinks mode rtl will set RTL mode on all vehicles.
* Use vehicle <n> to set the active vehicle

---
## ROS2 機器人作業系統
<img width="25%" height="20%" src="https://www.ros.org/imgs/humble.png">

### [Ubuntu 22.04 LTS install ROS2](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html#)
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

**ROS2 test run**<br>
* test Talker-Listern
  - On one terminal
```
source_ros2
ros2 run demo_nodes_cpp talker
```
  - In another terminal
```
source_ros2
ros2 run demo_nodes_py listener
```

* test multicasting
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

* test Turtlesim
  - turtlesim node
```
source_ros2
ros2 run turtlesim turtlesim_node
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtlesim_node.png?raw=true)


  - turtlesim teleop-keyboard
```
source_ros2
ros2 run turtlesim turtle_teleop_key
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim_turtle_teleop_key.png?raw=true)

  - topic echo
```
source_ros2
ros2 topic echo /turtle1/cmd_vel
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ros2_run_turtlesim.png?raw=true)

---
### [v4l2_camera](https://index.ros.org/r/v4l2_camera/)
A ROS2 camera driver using Video4Linux2 (V4L2)<br>
* Install ROS package<br>
`sudo apt-get install ros-humble-v4l2-camera`<br>

* Usage:<br>
  - `ros2 run v4l2_camera v4l2_camera_node`<br>
  - `ros2 run rqt_image_view rqt_image_view`<br>
  - `ros2 topic echo`<br>
    /raw-image
  - `ros2 node list`<br>
    /v4l2-camera<br>
  - `ros2 node info /v4l2-camera`<br>

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

