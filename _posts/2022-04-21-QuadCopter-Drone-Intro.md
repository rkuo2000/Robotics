---
layout: post
title: 四軸無人機介紹
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to QuadCopter Drone, Ardupilot, AutoPilot.

---
## Drone
[新手DIY多軸飛行器——我的第一架450無人機](https://www.gushiciku.cn/dl/0pOfe/zh-tw)
![](https://uav.jreyn.net/user/pages/04.quadcopter-design/step-7-electronics-selection/quad%20wiring.jpg)
QAV250穿越機套件
![](https://img.ruten.com.tw/s2/2/97/4e/21606776067918_533_m.jpg)

F450空拍機套件
<table>
<tr>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_16.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_500.jpg"></td>
</tr>
</table>

### 無人機電機
[無人機的電機電調你都了解嗎](https://ppfocus.com/0/dieeca43e.html)<br>

**電機的種類及區別**<br>
對於多旋翼無人機來說，小型無人機通常使用有刷電機，比如空心杯電機；而軸距較大，通常大於200mm左右的無人機都使用無刷電機。<br>
目前的無人機多以無刷電機 中的永磁同步電機爲主。<br>
無刷電機：可連續工作20000小時 左右，常規的使用壽命7-10年。<br>
有刷電機：可連續工作5000小時左右，常規的使用壽命2-3年。<br>

**電機的基本參數**<br>
最大電流（A），最大電壓（V），KV值。<br>
KV值：指電機在單位電壓下的轉速。一般KV值越高，代表電機的轉速越快。<br>
比方說：KV值爲1000，意思是：此電機在1V電壓下，每分鐘轉速爲1000轉。<br>

**電機的命名**<br>
四位數字，前兩位是定子的直徑，後兩位是定子的高度。如4108規格的電機，定子的直徑是41mm，高度是8mm。

**如何選配電機**<br>
多旋翼的電機最大拉力總和不應低於總重的1.5倍，最好是兩倍朝上。

**2212 950KV** for 四軸F450/F350
![](https://img.ruten.com.tw/s1/1/26/ab/21704181796523_243_m.jpg)

---
## [Ardupilot](https://ardupilot.org/)
Copter -- Plane -- Rover -- Sub -- Antenna Tracker
![](https://ardupilot.org/ardupilot/_images/home_ardupilot.jpg)

---
### Hardware
* **PixHawk**
  ![](https://ardupilot.org/ardupilot/_images/pixhawk_small.jpg)
  - Processor
    - 32-bit ARM Cortex M4 core with FPU
    - 168 Mhz/256 KB RAM/2 MB Flash
    - 32-bit failsafe co-processor
  - Sensors
    - MPU6000 as main accel and gyro
    - ST Micro 16-bit gyroscope
    - ST Micro 14-bit accelerometer/compass (magnetometer)
    - MEAS barometer
  - Power
    - Ideal diode controller with automatic failover
    - Servo rail high-power (7 V) and high-current ready
    -  All peripheral outputs over-current protected, all inputs ESD protected
  - Interfaces
    - 5x UART serial ports, 1 high-power capable, 2 with HW flow control
    - Spektrum DSM/DSM2/DSM-X Satellite input
    - Futaba S.BUS input (output not yet implemented)
    - PPM sum signal
    - RSSI (PWM or voltage) input
    - I2C, SPI, 2x CAN, USB
    - 3.3V and 6.6V ADC inputs
  - Dimensions
    - Weight 38 g (1.3 oz)
    - Width 50 mm (2.0”)
    - Height 15.5 mm (.6”)
    - Length 81.5 mm (3.2”)
* **APM2.8**
  ![](https://content.instructables.com/ORIG/FIS/KM5R/J3YPUEXT/FISKM5RJ3YPUEXT.jpg?auto=webp) 
  - Arduino Compatible!
  - Includes 3-axis gyro, accelerometer, along with a high-performance barometer
  - Onboard 4 MegaByte Dataflash chip for automatic datalogging
  - Optional off-board GPS, uBlox LEA-6H module with Compass.
  - One of the first open source autopilot systems to use Invensense’s 6 DoF Accelerometer/Gyro MPU-6000.
  - Barometric pressure sensor upgraded to MS5607, from Measurement Specialties.
  - Atmel’s ATMEGA2560 and ATMEGA32U-2 chips for processing and usb functions respectively.
  - Weight: 30g

---
### Firmware
![](https://ardupilot.org/ardupilot/_images/firmware_types.jpg)
**[Code](https://github.com/ArduPilot/ardupilot)**
* [ArduCopter](https://github.com/ArduPilot/ardupilot/tree/master/ArduCopter)
* [ArduPlane](https://github.com/ArduPilot/ardupilot/tree/master/ArduPlane)
* [ArduSub](https://github.com/ArduPilot/ardupilot/tree/master/ArduSub)
  
---
### Mission Planner
![](https://ardupilot.org/ardupilot/_images/mission_planner_spline_waypoint.jpg)

---
### [PX4](https://px4.io/)
PX4 is an open source flight control software for drones and other unmanned vehicles. 
Open Source Autopilotfor Drone Developers<br>
![](https://docs.px4.io/v1.12/assets/img/pixhawk4_main_aux_ports.ab72e7e9.jpg)
<iframe width="826" height="465" src="https://www.youtube.com/embed/gWtrka2mK7U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* **[Basic Concepts](https://docs.px4.io/v1.12/zh/getting_started/px4_basic_concepts.html)**<br>
* **[PX4 Autopilot](https://github.com/PX4/PX4-Autopilot)**<br>

---
### [ESP32copter](https://github.com/rkuo2000/arduino/tree/master/examples/Robot/EspCopter32)
![](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/DSC02360.jpg?raw=true)
![](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/DSC02364.jpg?raw=true)
![](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/DSC02375.jpg?raw=true)
* [Esp32Copter.ino](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/Esp32Copter.ino)<br>
* [pid.ino](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/pid.ino)<br>
* [rc.ino](https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/rc.ino)<br>

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

