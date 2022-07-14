---
layout: post
title: 四軸無人機介紹
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to QuadCopter Drone, Ardupilot, AutoPilot, Esp32Copter, Fixed-Wing UAV

---
## Quadcopter (四軸無人機)
* **VTOL (Vertical Take-Off and Landing)**<br>
  [剖析無人機發展關鍵因子-VTOL](https://www.ctimes.com.tw/DispCols/tw/%E7%84%A1%E4%BA%BA%E6%A9%9F/VTOL/1806011539CF.shtml)<br>

### How A Quadcopter Works Along With Propellers And Motors
![](https://www.dronezon.com/wp-content/uploads/2017/11/How-A-Quadcopter-Flies-Using-Propeller-And-Motor-Direction-e1580563822230.jpg)
![](https://www.researchgate.net/profile/Herman-Myburgh/publication/285595103/figure/fig2/AS:339777892175875@1458020770386/Quadcopter-states-a-Forward-motion-b-backwards-motion-c-movement-left-d.png)
Quadcopter states: (a) Forward motion; (b) backwards motion; (c) movement left; (d) movement right; (e) increase altitude; (f) decrease altitude; (g) leftwards rotation; (h) rightwards rotation.  

![](https://uav.jreyn.net/user/pages/04.quadcopter-design/step-7-electronics-selection/quad%20wiring.jpg)

---
### Q100 室內穿越機
<iframe width="996" height="560" src="https://www.youtube.com/embed/YhTbYbuW8KI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<table>
<tr>
<td>Q100室內穿越機四軸機架</td>
<td>8520 航模小電機 空心杯</tD>
<td>室內穿越微型有刷馬達驅動板</td>
</tr>
<tr>
<td><img src="https://img.ruten.com.tw/s1/5/48/23/21649673459747_114.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/d/c0/18/21805650628632_901.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/2/a8/88/21637601301640_510.jpg"></td>
</tr>
</table>

### QAV250 穿越機
![](https://img.ruten.com.tw/s2/2/97/4e/21606776067918_533_m.jpg)
<iframe width="996" height="560" src="https://www.youtube.com/embed/jXG91unOZts" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="996" height="560" src="https://www.youtube.com/embed/BDjCUj14Iyc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### F450空拍機
[新手DIY多軸飛行器——我的第一架450無人機](https://www.gushiciku.cn/dl/0pOfe/zh-tw)
<table>
<tr>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_16.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_500.jpg"></td>
</tr>
</table>
<iframe width="996" height="560" src="https://www.youtube.com/embed/cg1-L9EYe1U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### 自動避障航拍機
<iframe width="712" height="359" src="https://www.youtube.com/embed/DjWONLRgvZ0" title="【新手入門級】S91折疊無人機 自動避障航拍機【8K雙攝像頭+30分鐘長續航" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**<u>無人機功能</u>** :
1. 一鍵起飛
2. 三面避障
3. 前進避障
4. 左右避障
5. 前置鏡頭，底置鏡頭
6. 氣壓定高懸停
7. 實時圖傳 (鏡頭影像傳到手機顯示)
8. 手勢拍照/錄像
9. 軌跡飛行
10. 360度翻滾 
11. 無頭模式 (Headless)
12. 一鍵返航

---
### Coaxial Quadcopter
[Design and Model Predictive Control of a Mars Coaxial Quadrotor](https://arxiv.org/pdf/2109.06810.pdf)
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQD5bTakTcz6Xhbpj-42NgByQgAIoZefXLrUw&usqp=CAU)

---
### DelftAcopter
<iframe width="918" height="517" src="https://www.youtube.com/embed/wj0gV08Hdr8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Google Drone
<iframe width="1280" height="720" src="https://www.youtube.com/embed/7wA8uYjgfoM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### LONG-RANGE TACTICAL VTOL UAS (長程戰術垂直起降無人飛機系統)
VTOL (Vertical Take-Off and Landing)
UAS (Unmanned Aircraft Systems)
<iframe width="1120" height="630" src="https://www.youtube.com/embed/pV9iXIa6E9Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
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
### Flight Modes (飛行模式)
**Recommended Flight Modes:**<br>
* [Stabilize (穩定模式)](https://ardupilot.org/copter/docs/stabilize-mode.html#stabilize-mode)
* [Altitude Hold (維持高度模式)](https://ardupilot.org/copter/docs/altholdmode.html#altholdmode)
* [Loiter (閒逛模式)](https://ardupilot.org/copter/docs/loiter-mode.html#loiter-mode)
<iframe width="697" height="422" src="https://www.youtube.com/embed/yVAnBQkNJdY" title="Ardupilot:Copter V3.6.0 Release" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* [RTL (Return-to-Launch) (返回原點模式)](https://ardupilot.org/copter/docs/rtl-mode.html#rtl-mode)
![](https://ardupilot.org/copter/_images/RTL.jpg)
* [Auto](https://ardupilot.org/copter/docs/auto-mode.html#auto-mode)
![](https://ardupilot.org/copter/_images/auto.jpg)

**Additional Flight Modes:**<br>
* [Acro (競技模式)](https://ardupilot.org/copter/docs/acro-mode.html#acro-mode)
  - Release the sticks and the vehicle will maintain its current attitude and will not return to level (attitude hold).
* [AirMode](https://ardupilot.org/copter/docs/airmode.html#airmode)
* [Heli_Autorotate (自旋)](https://ardupilot.org/copter/docs/traditional-helicopter-autorotation-mode.html#traditional-helicopter-autorotation-mode) for traditional helicopters only.
* [AutoTune (自調)](https://ardupilot.org/copter/docs/autotune.html#autotune)
  - automatically tune the Stabilize P, Rate P and D, and maximum rotational acceleration
* [Brake (煞停)](https://ardupilot.org/copter/docs/brake-mode.html#brake-mode)
* [Circle (繞圈)](https://ardupilot.org/copter/docs/circle-mode.html#circle-mode)
* [Drift (漂移)](https://ardupilot.org/copter/docs/drift-mode.html#drift-mode)
* [Flip (翻滾)](https://ardupilot.org/copter/docs/flip-mode.html#flip-mode)
* [FlowHold (穩停)] (https://ardupilot.org/copter/docs/flowhold-mode.html#flowhold-mode)
  - FlowHold mode uses an [optical flow sensor](https://ardupilot.org/copter/docs/common-optical-flow-sensors-landingpage.html#common-optical-flow-sensors-landingpage) to hold position without the need for a GPS nor a downward facing Lidar.
* [Follow (跟隨)](https://ardupilot.org/copter/docs/follow-mode.html#follow-mode)
* [Guided](https://ardupilot.org/copter/docs/ac2_guidedmode.html#ac2-guidedmode) (and Guided_NoGPS)
* [Land (著陸)](https://ardupilot.org/copter/docs/land-mode.html#land-mode)
* [PosHold (維持位置)](https://ardupilot.org/copter/docs/poshold-mode.html#poshold-mode)
* [Sport](https://ardupilot.org/copter/docs/sport-mode.html#sport-mode)
* [Throw (拋飛)](https://ardupilot.org/copter/docs/throw-mode.html#throw-mode)
* [Follow Me (跟著我)](https://ardupilot.org/copter/docs/ac2_followme.html#ac2-followme)
* [Simple and Super Simple](https://ardupilot.org/copter/docs/simpleandsuper-simple-modes.html#simpleandsuper-simple-modes)
![](https://ardupilot.org/copter/_images/NormalControls.jpg)
![](https://ardupilot.org/copter/_images/SimpleModeControls.jpg)
![](https://ardupilot.org/copter/_images/SuperSimpleControls.jpg)
* [Smart RTL (Return-to-Launch) 回發射點](https://ardupilot.org/copter/docs/smartrtl-mode.html#smartrtl-mode)
* [SysID (System Identification) 系統識別](https://ardupilot.org/copter/docs/systemid-mode.html#systemid-mode)
* [Turtle](https://ardupilot.org/copter/docs/turtle-mode.html#turtle-mode)
* [ZigZag](https://ardupilot.org/copter/docs/zigzag-mode.html#zigzag-mode)
![](https://ardupilot.org/copter/_images/zigzag-auto.png)
* [Avoid_ADSB](https://ardupilot.org/copter/docs/common-ads-b-receiver.html#common-ads-b-receiver)
  - ADS-B (aka Automatic Dependent Surveillance Broadcast) (自動相關監視廣播)
 
---
### Flight Features (飛行功能)
For a full set of features see the [full parameter list](https://ardupilot.org/plane/docs/parameters.html) and the [MAVLink protocol definition](https://mavlink.io/en/).
* [Automatic Takeoff (自動起飛)](https://ardupilot.org/plane/docs/automatic-takeoff.html) 
  - Hand Launching (手拋發射)
  - Catapult Launching (發射器發射)
  - Bungee Launching (蹦極發射)
  - Runway Takeoffs (跑道起飛)
  - Testing Ground Takeoff in FBWA mode (Fly By Wire_A mode)
  - Speed Scaling Issues with no Airspeed Sensor 
* [Automatic Landing (自動降落)](https://ardupilot.org/plane/docs/automatic-landing.html) 
  - Setting Flare point (設定閃光點)
  - Controlling the glide slope (控制下滑坡道)
  - Landing Airspeed (降落空速)
  - Controlling the approach (控制著近)
  - Controlling the Flare (控制拉平)
  - After the Flare (拉平之後)
  - Using a rangefinder (使用測距儀)
* [Inverted Flight (顛倒飛行)](https://ardupilot.org/plane/docs/inverted-flight.html)
* [Stall Prevention (失速預防)](https://ardupilot.org/plane/docs/stall-prevention.html)
* [Geo-Fencing in Plane (地理圍欄)](https://ardupilot.org/plane/docs/common-geofencing-landing-page.html)
* [Terrain Following (地形跟隨)](https://ardupilot.org/plane/docs/common-terrain-following.html)
  - see Copter specific [terrain following instructions](https://ardupilot.org/copter/docs/terrain-following.html#terrain-following) here.
  - The ground station is normally responsible for providing the raw terrain data which is sent to the aircraft via MAVLink.
  - Terrain following works by maintaining a terrain database on the microSD card on the autopilot which gives the terrain height in meters above sea level for a grid of geographic locations.  
* [Soaring (翱翔)](https://ardupilot.org/plane/docs/soaring-4_1.html) 
![](https://ardupilot.org/plane/_images/thermalling.jpg)
* [Automated Aerobatics (自動化特技飛行)](https://ardupilot.org/plane/docs/common-scripting-aerobatics.html)
  - ArduPilot has the capability of executing aerobatics from a [LUA script](https://ardupilot.org/plane/docs/common-lua-scripts.html#common-lua-scripts)
* [Moving Vehicle/Ship Takeoff/Landing (移動載台之起飛與降落)](https://ardupilot.org/plane/docs/common-ship-landing.html) 
  - To use this feature you need a **beacon** setup on the landing platform.
  - The beacon will be broadcasting its position to allow the QuadPlane to track its moving HOME position, similar to Copter’s [Follow Mode (跟隨模式)](https://ardupilot.org/copter/docs/follow-mode.html#follow-mode).
  
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

---
## Fixed-Wing UAV

### [三角翼](https://www.ruten.com.tw/item/show?21932395978323)
![](https://img.ruten.com.tw/s1/f/ba/53/21932395978323_917.jpg)
* **飛行展示**
<iframe width="996" height="560" src="https://www.youtube.com/embed/dKQz6L-EHZI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* **水平校正**
<iframe width="996" height="560" src="https://www.youtube.com/embed/gPcyUXFmqwg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### MQ-9 Reaper
<iframe width="1280" height="720" src="https://www.youtube.com/embed/Nn_YexecBas" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
[MQ-9 掠奪者無人偵察機](https://www.ruten.com.tw/item/show?21437153985299)<br>
1. 翼展 : 3 公尺
2. 機身長 : 156 公分
3. 動力 : 20CC-30CC 引擎 
4. 馬達 : 400KV
5. 電池容量 : 22.2V 6000MAH - 10000mah
6. 電子變速器 : 100A
7. 螺旋槳 : 16 X 8 , 17 X 8 , 18 X 6
8. 飛行重量 : 5100 克


<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

