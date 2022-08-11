---
layout: post
title: 嵌入式開發板 - Raspberry
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

介紹樹莓派RPi4B,及使用 Ubuntu Desktop 22.04 LTS 作業系統(Real-Time), OpenCV-Python 影像處理, Pi-Camera與IMU 驅動程式, MAVlink(飛控板通訊), 及ROS2機器人作業系統.

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

### [Install Ubuntu on a Raspberry Pi](https://ubuntu.com/download/raspberry-pi)
Based on upstream v5.15, the 22.04 LTS kernel integrates the out-of-tree PREEMPT_RT patch for x86_64 and AArch64 architectures.<br>
1. get a SD card >= 16GB

2. Download [Ubuntu Desktop 22.04 LTS 64-bit](https://ubuntu.com/download/raspberry-pi/thank-you?version=22.04&architecture=desktop-arm64+raspi)<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/RPi4_Ubuntu2204_Desktop.png?raw=true)

3. write .img into SDcard by using **Win32DiskImager** or **balenaEtcher**

4. plugin SDcard & power up RPi4B

5. username: `ubuntu`, password: `ubuntu2204`

6. For fitting TV screen,<br>
`sudo nano /boot/firmware/config.txt`<br>
```
#disable_overscan = 1 
```

7. For using pi-camera (v1.3)<br>
`sudo nano /boot/firmware/config.txt`<br>

```
[all]
dtoverlay=vc4-kms-v3d
gpu_mem=512 
start_x=1

#camera_auto_detect=1
display_auto_detect=1
```

Reboot / Restart<br>
* To check camera:<br>
`ls -l /dev/video0`<br>
`v4l2-ctl --list-devices`<br>
   
---
### 作業系統更新
```
sudo apt update
sudo apt upgrade
```
* 安全地更新<br>
```
sudo apt install aptitude -y
sudo aptitude safe-upgrade
```
* 安裝SSH server<br>
`sudo apt install openssh-server -y`<br>

* 從PC remote login<br>
`ssh ubuntu@192.168.0.22`<br>
username ="bunutu", password="ubuntu2204"<br>

---
### 分享樹莓派之顯示輸出 
* 在PC上啟動X-server<br>
在PC上安裝 **[MobaXterm - Home edition (Free)](https://mobaxterm.mobatek.net/download.html)**<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/MobaXterm_logo.png?raw=true)

* 在RPi4B上修改.bashrc, 更改顯示輸出至PC X-server的位址<br>
`nano ~/.bashrc`<br>
```
export DISPLAY=192.168.0.13:0.0 #PC X-server IP address
export LIBGL_ALWAYS_INDIRECT=
export LIBGL_ALWAYS_SOFTWARE=1
``` 

* 在RPi4B上修改/dev/video0權限, 才能看到pi-camera輸出<br>
`sudo chmod 777 /dev/video0`<br>

---
### Python3 packages
`python3 -V`<br>
* 安裝 pip3<br>
`sudo apt-get install python3-pip`<br>
* 更新 pip3<br>
`pip3 install --upgrade pip`<br>

---
### [Control Raspberry Pi GPIO Pins from Python](https://www.ics.com/blog/control-raspberry-pi-gpio-pins-python#:~:text=Raspberry%20Pi%20model.-,RPi.,an%20MIT%20free%20software%20license.)
* 安裝RPi.GPIO<br>
`pip3 install RPi.GPIO`<br>

GPIO程式範例:<br>
```
#!/usr/bin/python3

import RPi.GPIO as GPIO
import time

led = 18
switch = 31

GPIO.setmode(GPIO.BOARD)
GPIO.setup(led, GPIO.OUT)
GPIO.setup(switch, GPIO.IN)

for i in range(10):
    GPIO.output(led, GPIO.HIGH)
    time.sleep(0.2)
    GPIO.output(led, GPIO.LOW)
    time.sleep(0.2)
    print('Switch status = ', GPIO.input(switch))

GPIO.cleanup()
```

---
### [Configuring I2C](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c)
* 安裝I2C工具<br>
`sudo apt-get install -y python3-smbus`<br>

* 偵測I2C裝置<br>
`sudo i2cdetect -y 1`<br>
![](https://cdn-learn.adafruit.com/assets/assets/000/003/055/medium800/learn_raspberry_pi_i2c-detect.png?1396790698)

---
## Image Processing

### Install OpenCV
* Install OpenCV on **Ubuntu 22.04** (RPi4B)<br>
`pip3 install opencv-contrib-python`<br>

* Install OpenCV on **Windows 11** (PC)
  - Install [Python for Windows](https://www.python.org/downloads/)
  - Install [Git for Windows](https://gitforwindows.org/)
  - Run Gitbash to install opencv-python<br>
    `pip3 install opencv-python`<br>

* Download [OpenCV 程式範例 ](https://github.com/rkuo2000/cv2)<br>
```
cd ~
git clone https://github.com/rkuo2000/cv2
cd ~/cv2
```

* 使用鏡頭 (Pi-camera / USB webcam)<br>
```
ls -l /dev/video0
cd ~/cv2
python3 cam.py
```

---
### Object Detection
[Detect Objects of Similar Color using OpenCV in Python](https://techvidvan.com/tutorials/detect-objects-of-similar-color-using-opencv-in-python/)<br>
![](https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2021/06/draw-contour.png)

---
### [Object Detection - Balls](https://www.bluetin.io/opencv/object-detection-tracking-opencv-python/)
[jpg_object_detection.py](https://github.com/rkuo2000/cv2/blob/master/jpg_object_detection.py)<br>
`python3 jpg_object_detection.py`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/cv2-object-detection-balls.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/cv2-object-detection-contours.png?raw=true)

---
### Object Tracking 
[cam_object_tracking.py](https://github.com/rkuo2000/cv2/blob/master/cam_object_tracking.py)<br>
* Usage:
```
cd ~/cv2
python3 cam_object_tracking.py 
```

* Change Color range<br>
1. use PaintBrush(小畫家) to find color range in **HSV** (挑兩個點找出綠色的範圍)
<table>
  <tr>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PaintBrush_HSV_Green1.png?raw=true"></td>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PaintBrush_HSV_Green2.png?raw=true"></td>
  </tr>
</table>
2. edit .py to adjust the color range<br>

  - Blue color  
```
lower_blue = np.array([100, 90, 90])
upper_blue = np.array([120,255,255])
```

  - Green color
```
lower_blue = np.array([ 50, 90, 90])
upper_blue = np.array([100,255,255])
```

---
### Landing Mark Detection
<table>
<tr>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H00.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H01.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H02.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H03.png?raw=true"></td>	
</tr>
</table>

[jpg_contours.py](https://github.com/rkuo2000/cv2/blob/master/copter/jpg_contours.py)<br>
```
import numpy as np
import sys
import cv2

if len(sys.argv)>1:
    filename = sys.argv[1]
else:
    filename = "H03.png"

image = cv2.imread(filename)
gray = cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)

blur = cv2.GaussianBlur(gray, (11,11), 0)
cv2.imshow("Blur", blur)

edge = cv2.Canny(blur, 30, 160)
cv2.imshow("Edge", edge)

(cnts, hierarchy) = cv2.findContours(edge,cv2.RETR_EXTERNAL,cv2.CHAIN_APPROX_SIMPLE)

# Draw all contours
cv2.drawContours(image, cnts, -1, (0,255,0), 1)

# draw center in yellow-dot
for c in cnts:
    M= cv2.moments(c)
    cX = int(M["m10"]/M["m00"])
    cY = int(M["m01"]/M["m00"])
    print(cX, cY)
    cv2.circle(image,(cX,cY), 5, (1,227,254), -1)

cv2.imshow("contours", image)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
**Exercises:**<br>
`cd ~/cv2/copter`<br>
* `python jpg_contours.py H00.png`<br>
![](https://github.com/rkuo2000/cv2/blob/master/copter/copter_contours_H00.png?raw=true)

* `python jpg_contours.py H03.png`<br>
![](https://github.com/rkuo2000/cv2/blob/master/copter/copter_contours_H03.png?raw=true)

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
## [ArUco](https://docs.opencv.org/4.6.0/d5/dae/tutorial_aruco_detection.html)
![](https://docs.opencv.org/4.6.0/markers.jpg)

An ArUco marker is a synthetic square marker composed by a wide black border and an inner binary matrix which determines its identifier (id). 
The marker size determines the size of the internal matrix. For instance a marker size of 4x4 is composed by 16 bits.<br>
A marker can be found rotated in the environment, however, the detection process needs to be able to determine its original rotation, so that each corner is identified unequivocally. This is also done based on the binary codification.<br>

**[Github:](https://github.com/GSNCodes/ArUCo-Markers-Pose-Estimation-Generation-Python)**<br>

```
cd ~
git clone https://github.com/rkuo2000/cv2
cd ~/cv2/ArUCo
```

---
### [ArUco markers generator](https://chev.me/arucogen/)
[generate_aruco_tags.py](https://github.com/rkuo2000/cv2/blob/master/ArUCo/generate_aruco_tags.py)<br>
`python3 generate_aruco_tags.py --id 24 --type DICT_5X5_100 -o tags/`<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/ArUco_markers_generator.png?raw=true)

**ArUco dictionaries:**
There are 21 different ArUco dictionaries built into the OpenCV library
```
ARUCO_DICT = 
	"DICT_4X4_50": cv2.aruco.DICT_4X4_50,
	"DICT_4X4_100": cv2.aruco.DICT_4X4_100,
	"DICT_4X4_250": cv2.aruco.DICT_4X4_250,
	"DICT_4X4_1000": cv2.aruco.DICT_4X4_1000,
	"DICT_5X5_50": cv2.aruco.DICT_5X5_50,
	"DICT_5X5_100": cv2.aruco.DICT_5X5_100,
	"DICT_5X5_250": cv2.aruco.DICT_5X5_250,
	"DICT_5X5_1000": cv2.aruco.DICT_5X5_1000,
	"DICT_6X6_50": cv2.aruco.DICT_6X6_50,
	"DICT_6X6_100": cv2.aruco.DICT_6X6_100,
	"DICT_6X6_250": cv2.aruco.DICT_6X6_250,
	"DICT_6X6_1000": cv2.aruco.DICT_6X6_1000,
	"DICT_7X7_50": cv2.aruco.DICT_7X7_50,
	"DICT_7X7_100": cv2.aruco.DICT_7X7_100,
	"DICT_7X7_250": cv2.aruco.DICT_7X7_250,
	"DICT_7X7_1000": cv2.aruco.DICT_7X7_1000,
	"DICT_ARUCO_ORIGINAL": cv2.aruco.DICT_ARUCO_ORIGINAL,
	"DICT_APRILTAG_16h5": cv2.aruco.DICT_APRILTAG_16h5,
	"DICT_APRILTAG_25h9": cv2.aruco.DICT_APRILTAG_25h9,
	"DICT_APRILTAG_36h10": cv2.aruco.DICT_APRILTAG_36h10,
	"DICT_APRILTAG_36h11": cv2.aruco.DICT_APRILTAG_36h11
}
```

### ArUCo Markers Detection
[detect_aruco_images.py](https://github.com/rkuo2000/cv2/blob/master/ArUCo/detect_aruco_images.py)<br>
* `python3 detect_aruco_images.py --image Images/test_image_1.png --type DICT_5X5_100` # Image file
![](https://github.com/rkuo2000/cv2/raw/master/ArUCo/Images/output_sample.png)

* `python3 detect_aruco_video.py --type DICT_5X5_100 --camera True` # WebCam

* `python3 detect_aruco_video.py --type DICT_5X5_100 --camera False --video test_video.mp4` # Video file

### ArUCo Pose Estimation
[pose_estimation.py](https://github.com/rkuo2000/cv2/blob/master/ArUCo/pose_estimation.py)<br>
* Calibration<br>
`python3 calibration.py --dir calibration_checkerboard/ --square_size 0.024`<br>
You need to have a folder containing a set of checkerboard images taken using your camera. Make sure that these checkerboard images are of different poses and orientation. You need to provide the path to this directory and the size of the square in metres. You can also change the shape of the checkerboard pattern using the parameters given. Make sure this matches with your checkerboard pattern. This code will generate two numpy files calibration_matrix.npy and distortion_coefficients.npy. These files are required to execute the next step that involves pose estimation.

* Pose Estimation<br>
`python3 pose_estimation.py --K_Matrix calibration_matrix.npy --D_Coeff distortion_coefficients.npy --type DICT_5X5_100`<br>
![](https://github.com/rkuo2000/cv2/raw/master/ArUCo/Images/pose_output.gif)

---
## [MAVlink](https://ardupilot.org/dev/docs/mavlink-commands.html)

### [MAVLink Basics](https://ardupilot.org/dev/docs/mavlink-basics.html)
![](https://ardupilot.org/dev/_images/mavlink-frame.png)
High Level Message Flow
![](https://ardupilot.org/dev/_images/mavlink-message-flow.png)

---
### [Copter Commands in Guided Mode](https://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html)

* [Arming and Disarming](https://ardupilot.org/dev/docs/mavlink-arming-and-disarming.html)
<table>
<tr><td>MAVProxy/SITL Command</td><td>Description</td></tr>
<tr><td>message COMMAND_LONG 0 0 400 0 1 0 0 0 0 0 0</td><td>arm the vehicle (may fail because of arming checks)</td></tr>
<tr><td>message COMMAND_LONG 0 0 400 0 1 21196 0 0 0 0 0</td><td>force arm the vehicle (try to bypass arming checks)</td></tr>
<tr><td>message COMMAND_LONG 0 0 400 0 0 0 0 0 0 0 0</td><td>disarm the vehicle (may fail if not landed)</td></tr>
<tr><td>message COMMAND_LONG 0 0 400 0 0 21196 0 0 0 0 0</td><td>force disarm the vehicle even if flying</td></tr>
<table>

**Movement Commands**<br>
* [SET_POSITION_TARGET_LOCAL_NED](https://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html#copter-commands-in-guided-mode-set-position-target-local-ned)
* [SET_POSITION_TARGET_GLOBAL_INT](https://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html#copter-commands-in-guided-mode-set-position-target-global-int)
* [SET_ATTITUDE_TARGET (supported in Guided and Guided_NoGPS modes)](https://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html#copter-commands-in-guided-mode-set-attitude-target)

**MAV_CMDs**<br>
* [MAV_CMD_PREFLIGHT_REBOOT_SHUTDOWN](https://mavlink.io/en/messages/common.html#MAV_CMD_PREFLIGHT_REBOOT_SHUTDOWN)
* [MAV_CMD_NAV_TAKEOFF](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-nav-takeoff)
* [MAV_CMD_NAV_LAND](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-nav-land)
* [MAV_CMD_NAV_RETURN_TO_LAUNCH](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-nav-return-to-launch)
* [MAV_CMD_CONDITION_YAW](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-condition-yaw)
* [MAV_CMD_DO_CHANGE_SPEED](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-do-change-speed)
* [MAV_CMD_DO_FLIGHTTERMINATION - disarms motors immediately (Copter falls!).](https://mavlink.io/en/messages/common.html#MAV_CMD_DO_FLIGHTTERMINATION)
* [MAV_CMD_DO_PARACHUTE](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-do-parachute)
* [MAV_CMD_DO_SET_ROI](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-do-set-roi)
* [MAV_CMD_NAV_LOITER_UNLIM](https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html#mav-cmd-nav-loiter-unlim)

* [Move a Servo](https://ardupilot.org/dev/docs/mavlink-move-servo.html)
Set the Servo position with MAV_CMD_DO_SET_SERVO
<table>
<tr><td>MAVProxy/SITL Command</td><td>Description</td></tr>
<tr><td>message COMMAND_LONG 0 0 183 0 8 1200 0 0 0 0 0</td><td>Move servo output 8 to 1200</td></tr>
<table>
	
---
### [Communicating with Raspberry Pi via MAVLink](https://ardupilot.org/dev/docs/raspberry-pi-via-mavlink.html)
Connect the flight controller’s **TELEM2** port to the RPi’s **TXD0**(GPIO14), **RXD0**(GPIO) and **Ground**  pins.

**Setting up the flight controller**<br>
Connect to the flight controller with a ground station (i.e. Mission Planner) and set the following parameters:<br>
* **SERIAL2_PROTOCOL** = 2 (the default) to enable MAVLink 2 on the serial port.
* **SERIAL2_BAUD** = 921 so the flight controller can communicate with the RPi at 921600 baud.
* **LOG_BACKEND_TYPE** = 3 if you are using APSync to stream the dataflash log files to the RPi

---
### MAVProxy
MAVProxy can be used to send commands to the flight controller from the Pi. It can also be used to route telemetry to other network endpoints.
This assumes you have a SSH connection to the Pi.<br>
```
sudo apt-get install python3-dev python3-opencv python3-wxgtk4.0 python3-pip python3-matplotlib python3-lxml python3-pygame
pip3 install PyYAML mavproxy --user
echo "export PATH=$PATH:$HOME/.local/bin" >> ~/.bashrc
```

* **Over USB**<br>
`pip3 install mavproxy pymavlink --user --upgrade`<br>

For Linux:<br>
`mavproxy.py --master=/dev/ttyUSB0`<br>
For Windows:<br> 
`mavproxy --master=COM14`<br>
For MacOS:<br>
`mavproxy.py --master=/dev/ttyusbserialxxx`<br>

* **Over Network**<br>
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

* **Startup Options**
```
mavproxy.py --master=/dev/ttyUSB0 --out=udp:192.168.1.1:14550
mavproxy.py --master=/dev/ttyACM0,115200 --out=/dev/ttyUSB0,57600
mavproxy.py --master=/dev/ttyACM0,115200 --out=COM17,57600
mavproxy.py --master=/dev/ttyACM0,57600 --out=udpbcast:192.168.2.255:14550
mavproxy.py --master=udpout:10.10.1.1:14550
mavproxy.py --master=tcpout:10.10.1.1:14550
mavproxy.py --master=/dev/ttyUSB0 --cmd="param load init.parm; module load map;"
```

---
### [pymavlink](https://github.com/ArduPilot/pymavlink)
[examples](https://www.ardusub.com/developers/pymavlink.html#run-pymavlink-on-the-companion-computer)<br>
* python
```
import pymavlink
print(pymavlink.__doc__)
```	

1. Autopilot connected to the computer via serial
```
from pymavlink import mavutil
master = mavutil.mavlink_connection("/dev/ttyACM0", baud=115200)
master.reboot_autopilot()
```
	
2. Run pyMavlink on the surface computer
```
import time
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')

# Make sure the connection is valid
master.wait_heartbeat()

# Get some information !
while True:
    try:
        print(master.recv_match().to_dict())
    except:
        pass
    time.sleep(0.1)	
```
{'mavpackettype': 'AHRS2', 'roll': -0.11364290863275528, 'pitch': -0.02841472253203392, 'yaw': 2.0993032455444336, 'altitude': 0.0, 'lat': 0, 'lng': 0}<br>
{'mavpackettype': 'AHRS3', 'roll': 0.025831475853919983, 'pitch': 0.006112074479460716, 'yaw': 2.1514968872070312, 'altitude': 0.0, 'lat': 0, 'lng': 0, 'v1': 0.0, 'v2': 0.0, 'v3': 0.0, 'v4': 0.0}<br>
{'mavpackettype': 'VFR_HUD', 'airspeed': 0.0, 'groundspeed': 0.0, 'heading': 123, 'throttle': 0, 'alt': 3.129999876022339, 'climb': 3.2699999809265137}<br>
{'mavpackettype': 'AHRS', 'omegaIx': 0.0014122836291790009, 'omegaIy': -0.022567369043827057, 'omegaIz': 0.02394154854118824, 'accel_weight': 0.0, 'renorm_val': 0.0, 'error_rp': 0.08894175291061401, 'error_yaw': 0.0990816056728363}	<br>
	
3. Run pyMavlink on the companion computer
```
import time
from pymavlink import mavutil

def wait_conn():
    """
    Sends a ping to stabilish the UDP communication and awaits for a response
    """
    msg = None
    while not msg:
        master.mav.ping_send(
            int(time.time() * 1e6), # Unix time in microseconds
            0, # Ping number
            0, # Request ping of all systems
            0 # Request ping of all components
        )
        msg = master.recv_match()
        time.sleep(0.5)	

master = mavutil.mavlink_connection('udpout:0.0.0.0:9000')
wait_conn()

# Get some information !
while True:
    try:
        print(master.recv_match().to_dict())
    except:
        pass
    time.sleep(0.1)	
```
{'mavpackettype': 'AHRS2', 'roll': -0.11364290863275528, 'pitch': -0.02841472253203392, 'yaw': 2.0993032455444336, 'altitude': 0.0, 'lat': 0, 'lng': 0}<br>
{'mavpackettype': 'AHRS3', 'roll': 0.025831475853919983, 'pitch': 0.006112074479460716, 'yaw': 2.1514968872070312, 'altitude': 0.0, 'lat': 0, 'lng': 0, 'v1': 0.0, 'v2': 0.0, 'v3': 0.0, 'v4': 0.0}<br>
{'mavpackettype': 'VFR_HUD', 'airspeed': 0.0, 'groundspeed': 0.0, 'heading': 123, 'throttle': 0, 'alt': 3.129999876022339, 'climb': 3.2699999809265137}<br>
{'mavpackettype': 'AHRS', 'omegaIx': 0.0014122836291790009, 'omegaIy': -0.022567369043827057, 'omegaIz': 0.02394154854118824, 'accel_weight': 0.0, 'renorm_val': 0.0, 'error_rp': 0.08894175291061401, 'error_yaw': 0.0990816056728363}<br>
	
4. Send Message to QGroundControl
```
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpout:localhost:14550', source_system=1)
master.mav.statustext_send(mavutil.mavlink.MAV_SEVERITY_NOTICE, "QGC will read this".encode())
```

5. Arm/Disarm the vehicle
```	
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

master.mav.command_long_send(master.target_system, master.target_component, mavutil.mavlink.MAV_CMD_COMPONENT_ARM_DISARM,  0,  1, 0, 0, 0, 0, 0, 0)
print("Waiting for the vehicle to arm")
master.motors_armed_wait()
print('Armed!')
	
master.mav.command_long_send(master.target_system, master.target_component, mavutil.mavlink.MAV_CMD_COMPONENT_ARM_DISARM,   0,  0, 0, 0, 0, 0, 0, 0)
master.motors_disarmed_wait()
```

6. Change flight mode
```
import sys
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

# Choose a mode
mode = 'STABILIZE'

# Check if mode is available
if mode not in master.mode_mapping():
    print('Unknown mode : {}'.format(mode))
    print('Try:', list(master.mode_mapping().keys()))
    sys.exit(1)

# Get mode ID
mode_id = master.mode_mapping()[mode]
# Set new mode
# master.mav.command_long_send(
#    master.target_system, master.target_component,
#    mavutil.mavlink.MAV_CMD_DO_SET_MODE, 0,
#    0, mode_id, 0, 0, 0, 0, 0) or:
# master.set_mode(mode_id) or:
master.mav.set_mode_send(master.target_system, mavutil.mavlink.MAV_MODE_FLAG_CUSTOM_MODE_ENABLED,  mode_id)

while True:
    # Wait for ACK command
    # Would be good to add mechanism to avoid endlessly blocking
    # if the autopilot sends a NACK or never receives the message
    ack_msg = master.recv_match(type='COMMAND_ACK', blocking=True)
    ack_msg = ack_msg.to_dict()

    # Continue waiting if the acknowledged command is not `set_mode`
    if ack_msg['command'] != mavutil.mavlink.MAV_CMD_DO_SET_MODE:
        continue

    # Print the ACK result !
    print(mavutil.mavlink.enums['MAV_RESULT'][ack_msg['result']].description)
    break
```

7. Send RC (Joystick)
```
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

def set_rc_channel_pwm(channel_id, pwm=1500):
    """ Set RC channel pwm value
    Args:
        channel_id (TYPE): Channel ID
        pwm (int, optional): Channel pwm value 1100-1900
    """
    if channel_id < 1 or channel_id > 18:
        print("Channel does not exist.")
        return

    # Mavlink 2 supports up to 18 channels: https://mavlink.io/en/messages/common.html#RC_CHANNELS_OVERRIDE
    rc_channel_values = [65535 for _ in range(18)]
    rc_channel_values[channel_id - 1] = pwm
    master.mav.rc_channels_override_send(
        master.target_system,                # target_system
        master.target_component,             # target_component
        *rc_channel_values)                  # RC channel list, in microseconds.

# Set some roll
set_rc_channel_pwm(2, 1600)

# Set some yaw
set_rc_channel_pwm(4, 1600)

# The camera pwm value sets the servo speed of a sweep from the current angle to
#  the min/max camera angle. It does not set the servo position.
# Set camera tilt to 45º (max) with full speed
set_rc_channel_pwm(8, 1900)

# Set channel 12 to 1500us
# This can be used to control a device connected to a servo output by setting the
# SERVO[N]_Function to RCIN12 (Where N is one of the PWM outputs)
set_rc_channel_pwm(12, 1500)
```

8. Send Manual Control
```
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

# Send a positive x value, negative y, negative z, positive rotation and no button.
# https://mavlink.io/en/messages/common.html#MANUAL_CONTROL
# Warning: Because of some legacy workaround, z will work between [0-1000]
# where 0 is full reverse, 500 is no output and 1000 is full throttle.
# x,y and r will be between [-1000 and 1000].
master.mav.manual_control_send( master.target_system,  500, -500,  250,  500,  0)

# To active button 0 (first button), 3 (fourth button) and 7 (eighth button)
# It's possible to check and configure this buttons in the Joystick menu of QGC
buttons = 1 + 1 << 3 + 1 << 7
master.mav.manual_control_send(master.target_system, 0,  0,  500,  0, buttons) # 500 means neutral throttle
```
	
9. Read all parameters
```	
import time
import sys
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

# Request all parameters
master.mav.param_request_list_send(master.target_system, master.target_component)
while True:
    time.sleep(0.01)
    try:
        message = master.recv_match(type='PARAM_VALUE', blocking=True).to_dict()
        print('name: %s\tvalue: %d' % (message['param_id'], message['param_value']))
    except Exception as error:
        print(error)
        sys.exit(0)
```

10. Read and write parameters
```
import time
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

master.mav.param_request_read_send( master.target_system, master.target_component, b'SURFACE_DEPTH', -1)

message = master.recv_match(type='PARAM_VALUE', blocking=True).to_dict()
print('name: %s\tvalue: %d' % (message['param_id'].decode("utf-8"), message['param_value']))

time.sleep(1)
master.mav.param_set_send( master.target_system, master.target_component, b'SURFACE_DEPTH', -12, mavutil.mavlink.MAV_PARAM_TYPE_REAL32)

# Read ACK
# IMPORTANT: The receiving component should acknowledge the new parameter value by sending a
# param_value message to all communication partners.
# This will also ensure that multiple GCS all have an up-to-date list of all parameters.
# If the sending GCS did not receive a PARAM_VALUE message within its timeout time,
# it should re-send the PARAM_SET message.
message = master.recv_match(type='PARAM_VALUE', blocking=True).to_dict()
print('name: %s\tvalue: %d' % (message['param_id'].decode("utf-8"), message['param_value']))

time.sleep(1)

# Request parameter value to confirm
master.mav.param_request_read_send(master.target_system, master.target_component, b'SURFACE_DEPTH', -1)

# Print new value in RAM
message = master.recv_match(type='PARAM_VALUE', blocking=True).to_dict()
print('name: %s\tvalue: %d' % (message['param_id'].decode("utf-8"), message['param_value']))	
```
	
11. Receive data and filter by message type
```
from pymavlink import mavutil
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')

while True:
    msg = master.recv_match()
    if not msg:
        continue
    if msg.get_type() == 'HEARTBEAT':
        print("\n\n*****Got message: %s*****" % msg.get_type())
        print("Message: %s" % msg)
        print("\nAs dictionary: %s" % msg.to_dict())
        # Armed = MAV_STATE_STANDBY (4), Disarmed = MAV_STATE_ACTIVE (3)
        print("\nSystem status: %s" % msg.system_status)
```

12. Request message interval
```
import time
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

def request_message_interval(message_id: int, frequency_hz: float):
    """
    Request MAVLink message in a desired frequency,
    documentation for SET_MESSAGE_INTERVAL:
        https://mavlink.io/en/messages/common.html#MAV_CMD_SET_MESSAGE_INTERVAL

    Args:
        message_id (int): MAVLink message ID
        frequency_hz (float): Desired frequency in Hz
    """
    master.mav.command_long_send(
        master.target_system, master.target_component,
        mavutil.mavlink.MAV_CMD_SET_MESSAGE_INTERVAL, 0,
        message_id, # The MAVLink message ID
        1e6 / frequency_hz, # The interval between two messages in microseconds. Set to -1 to disable and 0 to request default rate.
        0, 0, 0, 0, # Unused parameters
        0, # Target address of message stream (if message has target address fields). 0: Flight-stack default (recommended), 1: address of requestor, 2: broadcast.
    )
	
# Configure AHRS2 message to be sent at 1Hz
request_message_interval(mavutil.mavlink.MAVLINK_MSG_ID_AHRS2, 1)

# Configure ATTITUDE message to be sent at 2Hz
request_message_interval(mavutil.mavlink.MAVLINK_MSG_ID_ATTITUDE, 2)

# Get some information !
while True:
    try:
        print(master.recv_match().to_dict())
    except:
        pass
    time.sleep(0.1)
```

13. Control Camera Gimbal
```
import time
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

def look_at(tilt, roll=0, pan=0):
    """
    Moves gimbal to given position
    Args:
        tilt (float): tilt angle in centidegrees (0 is forward)
        roll (float, optional): pan angle in centidegrees (0 is forward)
        pan  (float, optional): pan angle in centidegrees (0 is forward)
    """
    master.mav.command_long_send(
        master.target_system,
        master.target_component,
        mavutil.mavlink.MAV_CMD_DO_MOUNT_CONTROL,
        1,
        tilt,
        roll,
        pan,
        0, 0, 0,
        mavutil.mavlink.MAV_MOUNT_MODE_MAVLINK_TARGETING)

# cycles the camera up and down
while True:
    for angle in range(-50, 50):
        look_at(angle*100)
        time.sleep(0.1)
    for angle in range(-50, 50):
        look_at(-angle*100)
        time.sleep(0.1)
```

14. Set Servo PWM
```
import time
from pymavlink import mavutil

def set_servo_pwm(servo_n, microseconds):
    """ Sets AUX 'servo_n' output PWM pulse-width.

    Uses https://mavlink.io/en/messages/common.html#MAV_CMD_DO_SET_SERVO

    'servo_n' is the AUX port to set (assumes port is configured as a servo).
        Valid values are 1-3 in a normal BlueROV2 setup, but can go up to 8
        depending on Pixhawk type and firmware.
    'microseconds' is the PWM pulse-width to set the output to. Commonly
        between 1100 and 1900 microseconds.

    """
    # master.set_servo(servo_n+8, microseconds) or:
    master.mav.command_long_send(
        master.target_system, master.target_component,
        mavutil.mavlink.MAV_CMD_DO_SET_SERVO,
        0,            # first transmission of this command
        servo_n + 8,  # servo instance, offset by 8 MAIN outputs
        microseconds, # PWM pulse-width
        0,0,0,0,0     # unused parameters
    )

# Create the connection
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
# Wait a heartbeat before sending commands
master.wait_heartbeat()

# command servo_1 to go from min to max in steps of 50us, over 2 seconds
for us in range(1100, 1900, 50):
    set_servo_pwm(1, us)
    time.sleep(0.125)	
```

15. Advanced Servo/Gripper Example
```
from pymavlink import mavutil

class RawServoOutput:
    """ A class for commanding a mavlink-controlled servo output port. """
    # https://mavlink.io/en/messages/common.html#MAV_CMD_DO_SET_SERVO
    CMD_SET = mavutil.mavlink.MAV_CMD_DO_SET_SERVO

    def __init__(self, master, instance, pwm_limits=(1100, 1500, 1900),
                 set_default=True):
        """ Initialise a RawServoOutput instance.

        'master' is a mavlink connection
        'instance' is the servo output (e.g. Pixhawk MAIN 1-8, AUX 9-16)
        'pwm_limits' is a tuple of min, default, and max pwm pulse-widths
            in microseconds (default (1100, 1500, 1900)).
        'set_default' is a boolean specifying whether to command the output
            to the specified default pulse-width (default True).

        """
        self.master     = master
        self.instance   = instance
        self.min_us, self._current, self.max_us = pwm_limits
        self._diff      = self.max_us - self.min_us

        if set_default:
            self.set_direct(self._current)

    def set_direct(self, us):
        """ Directly set the PWM pulse width.

        'us' is the PWM pulse width in microseconds.
            Must be between self.min_us and self.max_us.

        """
        assert self.min_us <= us <= self.max_us, "Invalid input value."

        # self.master.set_servo(self.instance, us) or:
        self.master.mav.command_long_send(
            self.master.target_system, self.master.target_component,
            self.CMD_SET,
            0, # first transmission of this command
            self.instance, us,
            0,0,0,0,0 # unused parameters
        )
        self._current = us
	
    def set_ratio(self, proportion):
        """ Set the PWM pulse-width ratio (auto-scale between min and max).

        'proportion' is a 0-1 value, where 0 corresponds to self.min_us, and
            1 corresponds to self.max_us.

        """
        self.set_direct(proportion * self._diff + self.min_us)

    def inc(self, us=50):
        """ Increment the PWM pulse width by 'us' microseconds. """
        self.set_direct(max(self.max_us, self._current+us))

    def dec(self, us=50):
        """ Decrement the PWM pulse width by 'us' microseconds. """
        self.set_direct(min(self.min_us, self._current-us))

    def set_min(self):
        """ Set the PWM to self.min_us. """
        self.set_ratio(0)

    def set_max(self):
        """ Set the PWM to self.max_us. """
        self.set_ratio(1)
	
    def center(self):
        """ Set the PWM to half-way between self.min_us and self.max_us. """
        self.set_ratio(0.5)
	
class AuxServoOutput(RawServoOutput):
    """ A class representing a mavlink-controlled auxiliary servo output. """
    def __init__(self, master, servo_n, main_outputs=8, **kwargs):
        """ Initiliase a servo instance.

        'master' is a mavlink connection.
        'servo_n' is one of the auxiliary servo outputs, like the servo_n
            outputs with QGroundControl joystick control.
            Most likely a value between 1-3, but possibly up to 6 or 8
            depending on setup.
        'main_outputs' is the number of MAIN outputs are present on the
            autopilot device (default 8).
        **kwargs are passed to RawServoOutput.

        """
        super().__init__(master, servo_n+main_outputs, **kwargs)
        self._main_outputs = main_outputs

    @property
    def servo_n(self):
        """ Return the AUX servo number of this output. """
        return self.instance - self._main_outputs

class Gripper(AuxServoOutput):
    """ A class representing a Blue Robotics' gripper. """
    def __init__(self, master, servo_n, pwm_limits=(1100, 1100, 1500),
                 **kwargs):
        """ Initialise a Gripper instance.

        'master' is a mavlink connection.
        'servo_n' is one of the auxiliary servo outputs, like the servo_n
            outputs with QGroundControl joystick control.
            Most likely a value between 1-3, but possibly up to 6 or 8
            depending on setup.
        'pwm_limits' is a tuple of min, default, and max pwm pulse-widths
            in microseconds (default (1100, 1100, 1900)).
        **kwargs are passed to AuxServoOutput.

        """
        super().__init__(master, servo_n, pwm_limits=pwm_limits, **kwargs)

    def open(self):
        """ Command the gripper to open. """
        self.set_max()

    def close(self):
        """ Command the gripper to close. """
        self.set_min()
	
if __name__ == '__main__':
    from time import sleep

    # Connect to the autopilot (pixhawk) from the surface computer,
    #  via the companion.
    autopilot = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
    # Wait for a heartbeat from the autopilot before sending commands
    autopilot.wait_heartbeat()

    # create a gripper instance on servo_1 (AUX output 1)
    gripper = Gripper(autopilot, 1)

    # open and close the gripper a few times
    for _ in range(3):
        gripper.open()
        sleep(2)
        gripper.close()
        sleep(1)	
```

16. Set Target Depth/Attitude
```
import time
import math
from pymavlink import mavutil
from pymavlink.quaternion import QuaternionBase

def set_target_depth(depth):
    """ Sets the target depth while in depth-hold mode.
    Uses https://mavlink.io/en/messages/common.html#SET_POSITION_TARGET_GLOBAL_INT
    'depth' is technically an altitude, so set as negative meters below the surface
        -> set_target_depth(-1.5) # sets target to 1.5m below the water surface.
    """
    master.mav.set_position_target_global_int_send(
        int(1e3 * (time.time() - boot_time)), # ms since boot
        master.target_system, master.target_component,
        coordinate_frame=mavutil.mavlink.MAV_FRAME_GLOBAL_INT,
        type_mask=( # ignore everything except z position
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_X_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_Y_IGNORE |
            # DON'T mavutil.mavlink.POSITION_TARGET_TYPEMASK_Z_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_VX_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_VY_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_VZ_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_AX_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_AY_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_AZ_IGNORE |
            # DON'T mavutil.mavlink.POSITION_TARGET_TYPEMASK_FORCE_SET |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_YAW_IGNORE |
            mavutil.mavlink.POSITION_TARGET_TYPEMASK_YAW_RATE_IGNORE
        ), lat_int=0, lon_int=0, alt=depth, # (x, y WGS84 frame pos - not used), z [m]
        vx=0, vy=0, vz=0, # velocities in NED frame [m/s] (not used)
        afx=0, afy=0, afz=0, yaw=0, yaw_rate=0
        # accelerations in NED frame [N], yaw, yaw_rate
        #  (all not supported yet, ignored in GCS Mavlink)
    )

def set_target_attitude(roll, pitch, yaw):
    """ Sets the target attitude while in depth-hold mode.
    'roll', 'pitch', and 'yaw' are angles in degrees.
    """
    master.mav.set_attitude_target_send(
        int(1e3 * (time.time() - boot_time)), # ms since boot
        master.target_system, master.target_component,
        # allow throttle to be controlled by depth_hold mode
        mavutil.mavlink.ATTITUDE_TARGET_TYPEMASK_THROTTLE_IGNORE,
        # -> attitude quaternion (w, x, y, z | zero-rotation is 1, 0, 0, 0)
        QuaternionBase([math.radians(angle) for angle in (roll, pitch, yaw)]),
        0, 0, 0, 0 # roll rate, pitch rate, yaw rate, thrust
    )

# Create the connection
master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
boot_time = time.time()
# Wait a heartbeat before sending commands
master.wait_heartbeat()

# arm ArduSub autopilot and wait until confirmed
master.arducopter_arm()
master.motors_armed_wait()

# set the desired operating mode
DEPTH_HOLD = 'ALT_HOLD'
DEPTH_HOLD_MODE = master.mode_mapping()[DEPTH_HOLD]
while not master.wait_heartbeat().custom_mode == DEPTH_HOLD_MODE:
    master.set_mode(DEPTH_HOLD)

# set a depth target
set_target_depth(-0.5)

# go for a spin
# (set target yaw from 0 to 500 degrees in steps of 10, one update per second)
roll_angle = pitch_angle = 0
for yaw_angle in range(0, 500, 10):
    set_target_attitude(roll_angle, pitch_angle, yaw_angle)
    time.sleep(1) # wait for a second

# spin the other way with 3x larger steps
for yaw_angle in range(500, 0, -30):
    set_target_attitude(roll_angle, pitch_angle, yaw_angle)
    time.sleep(1)

# clean up (disarm) at the end
master.arducopter_disarm()
master.motors_disarmed_wait()
```

17. Send GPS position
```
import time
from pymavlink import mavutil

master = mavutil.mavlink_connection('udpin:0.0.0.0:14550')
master.wait_heartbeat()

# GPS_TYPE need to be MAV
while True:
    time.sleep(0.2)
    master.mav.gps_input_send(
        0,  # Timestamp (micros since boot or Unix epoch)
        0,  # ID of the GPS for multiple GPS inputs
        # Flags indicating which fields to ignore (see GPS_INPUT_IGNORE_FLAGS enum).
        # All other fields must be provided.
        (mavutil.mavlink.GPS_INPUT_IGNORE_FLAG_VEL_HORIZ |
         mavutil.mavlink.GPS_INPUT_IGNORE_FLAG_VEL_VERT |
         mavutil.mavlink.GPS_INPUT_IGNORE_FLAG_SPEED_ACCURACY),
        0,  # GPS time (milliseconds from start of GPS week)
        0,  # GPS week number
        3,  # 0-1: no fix, 2: 2D fix, 3: 3D fix. 4: 3D with DGPS. 5: 3D with RTK
        0,  # Latitude (WGS84), in degrees * 1E7
        0,  # Longitude (WGS84), in degrees * 1E7
        0,  # Altitude (AMSL, not WGS84), in m (positive for up)
        1,  # GPS HDOP horizontal dilution of position in m
        1,  # GPS VDOP vertical dilution of position in m
        0,  # GPS velocity in m/s in NORTH direction in earth-fixed NED frame
        0,  # GPS velocity in m/s in EAST direction in earth-fixed NED frame
        0,  # GPS velocity in m/s in DOWN direction in earth-fixed NED frame
        0,  # GPS speed accuracy in m/s
        0,  # GPS horizontal accuracy in m
        0,  # GPS vertical accuracy in m
        7   # Number of satellites visible.
    )
```

18. Send rangefinder/computer vision distance measurement to the autopilot
```
import time
from pymavlink import mavutil

# Wait for server connection
def wait_conn():
    """
    Sends a ping to the autopilot to stabilish the UDP connection and waits for a reply
    """
    msg = None
    while not msg:
        master.mav.ping_send(
            int(time.time() * 1e6), # Unix time in microseconds
            0, # Ping number
            0, # Request ping of all systems
            0 # Request ping of all components
        )
        msg = master.recv_match()
        time.sleep(0.5)
	
# Send a ping to start connection and wait for any reply.	
master = mavutil.mavlink_connection('udpout:localhost:9000')
wait_conn()
	
master.mav.param_set_send(  1,  1,  b"RNGFND_TYPE", 10, mavutil.mavlink.MAV_PARAM_TYPE_INT8)

min_measurement = 10 # minimum valid measurement that the autopilot should use
max_measurement = 40 # maximum valid measurement that the autopilot should use
distance = 20 # You will need to supply the distance measurement
sensor_type = mavutil.mavlink.MAV_DISTANCE_SENSOR_UNKNOWN
sensor_id = 1
orientation = mavutil.mavlink.MAV_SENSOR_ROTATION_PITCH_270 # downward facing
covariance = 0

tstart = time.time()
while True:
    time.sleep(0.5)
    master.mav.distance_sensor_send(
        int((time.time() - tstart) * 1000),
        min_measurement,
        max_measurement,
        distance,
        sensor_type,
        sensor_id,
        orientation,
        covariance)	
```
	
---
### [MAVROS](https://github.com/mavlink/mavros/)
MAVLink extendable communication node for ROS.<br>

**Installation**<br>
```	
source_ros2
sudo apt-get install ros-humble-mavros ros-humble-mavros-extras	
wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
chmod +x install_geographiclib_datasets.sh
./install_geographiclib_datasets.sh
```

`ros2 run mavros mavros_node`<br>
`ros2 run mavros mavros_node _fcu_url:=/dev/ttyACM0:921600 _gcs_url:=udp://@172.16.254.1`<br>
	
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
`ros2 run v4l2_camera v4l2_camera_node`<br>
`ros2 run rqt_image_view rqt_image_view`<br>
`ros2 topic echo`<br>
/raw-image
`ros2 node list`<br>
/v4l2-camera<br>
`ros2 node info /v4l2-camera`<br>

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

