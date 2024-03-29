---
layout: post
title: Raspberry Pi 
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
![](https://github.com/rkuo2000/Robotics/blob/main/images/RPi4_Ubuntu2204_Desktop.png?raw=true)

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

* set as Wireless AP
[How to use your Raspberry Pi as a wireless access point](https://thepi.io/how-to-use-your-raspberry-pi-as-a-wireless-access-point/)<br>

---
### 分享樹莓派之顯示輸出 
* 在PC上啟動X-server<br>
在PC上安裝 **[MobaXterm - Home edition (Free)](https://mobaxterm.mobatek.net/download.html)**<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/MobaXterm_logo.png?raw=true)

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
![](https://github.com/rkuo2000/Robotics/blob/main/images/cv2-object-detection-balls.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/main/images/cv2-object-detection-contours.png?raw=true)

---
### Object Tracking 
[cam_object_tracking.py](https://github.com/rkuo2000/cv2/blob/master/cam_object_tracking.py)<br>

* Usage:<br>
```
cd ~/cv2
python3 cam_object_tracking.py 
```

* Change Color range<br>
1. use PaintBrush(小畫家) to find color range in **HSV** (挑兩個點找出綠色的範圍)
<table>
  <tr>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/main/images/PaintBrush_HSV_Green1.png?raw=true"></td>
    <td><img src="https://github.com/rkuo2000/Robotics/blob/main/images/PaintBrush_HSV_Green2.png?raw=true"></td>
  </tr>
</table>
2. edit .py to adjust the color range<br>

  - Blue color  
```
lower_bound = np.array([100, 90, 90])
upper_bound = np.array([120,255,255])
```

  - Green color
```
lower_bound = np.array([ 50, 90, 90])
upper_bound = np.array([100,255,255])
```

---
### Landing Mark Detection
![](https://github.com/rkuo2000/cv2/blob/master/copter/TDK26th_map.png?raw=true)
<table>
<tr>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H00.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H01.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H02.png?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/H03.png?raw=true"></td>	
</tr>
<tr>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/red_light.jpg?raw=true"></td>
<td><img src="https://github.com/rkuo2000/cv2/blob/master/copter/green_light.jpg?raw=true"></td>
</tr>
</table>

[jpg_object_detect.py](https://github.com/rkuo2000/cv2/blob/master/copter/jpg_object_detect.py)<br>
[cam_object_detect.py](https://github.com/rkuo2000/cv2/blob/master/copter/cam_object_detect.py)<br>

```
import cv2
import sys
import numpy as np

if len(sys.argv) >1:
    vid = int(sys.argv[1])
else:
    vid = 0
cap = cv2.VideoCapture(vid)

while(cap.isOpened()):
    ret, frame = cap.read()
    #frame = cv2.flip(frame, 1) # 0: vertical flip, 1: horizontal flip

    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)

    # lower & upper bound for any color
    lower_bound = np.array([  0,  90,  90])
    upper_bound = np.array([255, 255, 255])
    mask = cv2.inRange(hsv, lower_bound, upper_bound)

    # Bitwise-AND mask and original image
    res = cv2.bitwise_and(frame, frame, mask=mask)
    #cv2.imshow('RESULT', res)

    # Find Contours
    contours, hierarchy = cv2.findContours(mask, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

    # Finding The Largest Contour
    contour_sizes = [(cv2.contourArea(contour), contour) for contour in contours]
    biggest_contour = max(contour_sizes, key=lambda x: x[0])[1]

    # Bounding Rectangle
    x,y,w,h = cv2.boundingRect(biggest_contour)
    cv2.rectangle(frame,(x,y),(x+w,y+h),(0,255,0),2)
    cX = int(x + w/2)
    cY = int(y + h/2)
    cv2.circle(frame,(cX, cY), 5, (1,227,254), -1)
    cv2.imshow('Bounding BOX', frame)

    print(x,y,w,h)
    print(cX,cY)

    if cv2.waitKey(10) & 0xFF == ord('q'):
        break
        
cap.release()
cv2.destroyAllWindows()
```

**Exercises:**<br>
`cd ~/cv2/copter`<br>
* `python jpg_object_detect.py H00.png`<br>
* `python jpg_object_detect.py red_light.png`<br>
* `python jpg_object_detect.py green_light.png`<br>
* `python cam_object_detect.py`<br>


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

* [cam_optical_flow_sparse.py](https://github.com/rkuo2000/cv2/blob/master/copter/cam_optical_flow_sparse.py) 顯示第一個特徵點的光跡

```
import sys
import cv2
import numpy as np

if len(sys.argv) >1:
    vid = int(sys.argv[1])
else:
    vid = 0
cap = cv2.VideoCapture(vid)
   
# Parameters for Shi-Tomasi corner detection
feature_params = dict(maxCorners = 300, qualityLevel = 0.2, minDistance = 2, blockSize = 7)
#feature_params = dict(maxCorners = 100, qualityLevel = 0.3, minDistance = 7, blockSize = 7)
# Parameters for Lucas-Kanade optical flow
lk_params = dict(winSize = (15,15), maxLevel = 2, criteria = (cv2.TERM_CRITERIA_EPS | cv2.TERM_CRITERIA_COUNT, 10, 0.03))

color = np.random.randint(0,255,(300,3)) # Create some random colors
ret, old_frame = cap.read()
hsv = cv2.cvtColor(old_frame, cv2.COLOR_BGR2HSV)
lower_bound = np.array([  0,  90,  90])
upper_bound = np.array([255, 255, 255])
roi = cv2.inRange(hsv, lower_bound, upper_bound)
hsv = cv2.bitwise_and(old_frame, old_frame, mask=roi)
bgr = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)
prev_gray = cv2.cvtColor(bgr, cv2.COLOR_BGR2GRAY)
prev = cv2.goodFeaturesToTrack(prev_gray, mask = None, **feature_params)
mask = np.zeros_like(old_frame)

while(cap.isOpened()):
    ret, frame = cap.read() # capture a frame    
    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)
    lower_bound = np.array([  0,  90,  90])
    upper_bound = np.array([255, 255, 255])
    roi = cv2.inRange(hsv, lower_bound, upper_bound)
    #cv2.imshow('ROI', roi)
    hsv = cv2.bitwise_and(frame, frame, mask=roi)
    bgr = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)
    #cv2.imshow('BGR', bgr)
    gray = cv2.cvtColor(bgr, cv2.COLOR_BGR2GRAY)
    	
    next, status, error = cv2.calcOpticalFlowPyrLK(prev_gray, gray, prev, None, **lk_params)

    good_old = prev[status == 1] # Selects good feature points for previous position
    good_new = next[status == 1] # Selects good feature points for next position
    # Draws the optical flow tracks
    for i, (new, old) in enumerate(zip(good_new, good_old)):
        if i==0:
            a, b = new.ravel() # Returns a contiguous flattened array as (x, y) coordinates for new point
            c, d = old.ravel() # Returns a contiguous flattened array as (x, y) coordinates for old point
            mask  = cv2.line(mask, (int(a), int(b)), (int(c), int(d)), color[i].tolist(), 2)
            frame = cv2.circle(frame, (int(a), int(b)), 5, color[i].tolist(), -1)
    img = cv2.add(frame, mask)
    prev_gray = gray.copy()
    prev = good_new.reshape(-1, 1, 2)
    cv2.imshow("optical-flow sparse", img)

    if cv2.waitKey(10) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
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
![](https://github.com/rkuo2000/Robotics/blob/main/images/ArUco_markers_generator.png?raw=true)

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
</table>

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
</table>
	
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
`pip install pymavlink`<br>

[examples](https://www.ardusub.com/developers/pymavlink.html#run-pymavlink-on-the-companion-computer)<br>
`python`<br>
```
import pymavlink
print(pymavlink.__doc__)
```	

1. Autopilot connected to the computer via serial<br>
```
from pymavlink import mavutil
master = mavutil.mavlink_connection("/dev/ttyACM0", baud=115200)
master.reboot_autopilot()
```

---
### [DroneKit Channel Override](https://dronekit-python.readthedocs.io/en/latest/examples/channel_overrides.html)
```
pip install dronekit
git clone http://github.com/dronekit/dronekit-python.git
cd drone-kit-python
cd dronekit-python/examples/channel_overrides/
```

[channel_overrides.py](https://github.com/dronekit/dronekit-python/blob/master/examples/channel_overrides/channel_overrides.py)<br>

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
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim_turtlesim_node.png?raw=true)


  - turtlesim teleop-keyboard
```
source_ros2
ros2 run turtlesim turtle_teleop_key
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim_turtle_teleop_key.png?raw=true)

  - topic echo
```
source_ros2
ros2 topic echo /turtle1/cmd_vel
```
![](https://github.com/rkuo2000/Robotics/blob/main/images/ros2_run_turtlesim.png?raw=true)

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

---
## 機器人競賽

### [第26屆TDK盃全國大專校院創思設計與製作競賽](https://tdk.stust.edu.tw/)
[26TH TDK盃飛行組題目](https://tdk.stust.edu.tw/index.php?inter=module&id=8&did=13)  [Rules](https://tdk.stust.edu.tw/upload/module/files/26th%20TDK%E7%9B%83%E9%A3%9B%E8%A1%8C%E7%B5%84%E7%AB%B6%E8%B3%BD%E8%A6%8F%E5%89%87_0519%E6%9B%B4%E6%96%B0.pdf)<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/TDK26th_map.png?raw=true)

<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

