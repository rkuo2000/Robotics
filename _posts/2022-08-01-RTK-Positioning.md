---
layout: post
title: RTK Positioning
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---
 
Introduction to Real-Time Kinematic (RTK) Positioning, and Ublox Neo-M8P series.

---
## RTK Positioning
即時動態定位技術: 利用衛星達到即時精準定位的一種技術，方式為同時在參考站與移動站接 收衛星資料，透過通訊設備，將參考站的觀測資料傳送給移動站，移動站再透過差分計算，可以在移動時即時獲得精確的定位坐標。<br>

Real-time kinematic positioning (RTK) is the application of surveying to correct for common errors in current satellite navigation (GNSS) systems. It uses measurements of the phase of the signal's carrier wave in addition to the information content of the signal and relies on a single reference station or interpolated virtual station to provide real-time corrections, providing up to **centimetre-level accuracy**.<br>
<iframe width="837" height="470" src="https://www.youtube.com/embed/1allNivwgHI" title="無人機RTK定位技術簡介" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [Introduction to Network RTK](http://www.wasoft.de/e/iagwg451/intro/introduction.html)<br>
![](http://www.wasoft.de/e/iagwg451/intro/vrs.gif)

**Paper:** [Network Real Time Kinematic (NRTK) Positioning – Description, Architectures and Performances](https://www.researchgate.net/profile/Marco-Piras-2/publication/282339192_Network_Real_Time_Kinematic_NRTK_Positioning_-_Description_Architectures_and_Performances/links/572f487b08aeb1c73d13a0c2/Network-Real-Time-Kinematic-NRTK-Positioning-Description-Architectures-and-Performances.pdf)<br>

---
## Ublox
### [NEO-M8P series](https://www.u-blox.com/en/product/neo-m8p-series)
![](https://www.mouser.tw/images/marketingid/2020/np/170703669.jpg)
u-blox M8 high precision GNSS modules<br>
* NEO-M8P-0 : u-blox M8 high precision module with rover functionality
* NEO-M8P-2 : u-blox M8 high precision module with rover and base station functionality
* [NEO-M8P Product Summary](https://content.u-blox.com/sites/default/files/NEO-M8P_ProductSummary_%28UBX-15015836%29.pdf)
* [NEO-M8P Data Sheet]()
* [NEO-M8P Hardware Integration Manual]()

---
### AppBoards
* [C94-M8P AppBoard](https://www.u-blox.com/en/product/c94-m8p) : u-blox RTK application board package
  - [C94-M8P AppBoard User Guide](https://content.u-blox.com/sites/default/files/C94-M8P-AppBoard_UserGuide_%28UBX-15031066%29.pdf)
![](https://content.u-blox.com/sites/default/files/products/C94-M8P-4-CI.png) 
![](https://portal.u-blox.com/sfc/servlet.shepherd/version/renditionDownload?rendition=THUMB720BY480&versionId=0682p000006YxJY&operationContext=CHATTER&contentId=05T2p00000J3YbW&page=0)
  - [DigiKey C94-M8P-2](https://www.digikey.tw/en/products/detail/u-blox/C94-M8P-2/6150728)
![](https://media.digikey.com/photos/U-Blox%20America/C94-M8P.jpg)

* [SparkFun GPS-RTK Board - NEO-M8P-2](https://www.ruten.com.tw/item/show?21913448174138)
![](https://github.com/rkuo2000/Robotics/blob/main/images/NEO-M8P-2_SparkFun_GPS-RTK_Board.png?raw=true)

* [Neo-M8P RTK GNSS receiver board with SMA](https://www.gnss.store/neo-m8p-gnss-modules/90-ublox-neo-m8p-rtk-gnss-receiver-board-with-sma-base-or-rover.html)
![](https://github.com/rkuo2000/Robotics/blob/main/images/NEO-M8P_RTK_GNSS_receiver_board_with_SMA.png?raw=true)

* [Drotek RTK GNSS modules](https://drotek.gitbook.io/rtk-positioning-solutions/)
![](https://github.com/rkuo2000/Robotics/blob/main/images/Neo-M8P_Drotek_RTK_GNSS_modules.png?raw=true)

---
### [u-center](https://www.u-blox.com/en/product/u-center)
GNSS evaluation software for Windows<br>
![](https://content.u-blox.com/sites/default/files/products/u-center2_web.png)
![](https://content.u-blox.com/sites/default/files/products/u-center.png)
![](https://content.u-blox.com/sites/default/files/2022-03/u-center-product-selector.jpg)
* For M10 products only : [u-center 2](https://u-center2-updates.u-blox.com/u-center2-installer.exe?_ga=2.166793531.441583464.1657687777-673334558.1657687777), [User Guide](https://www.u-blox.com/en/info/u-center-2-user-guide)  
* For M9 products and below: [U-Center v22.05](https://content.u-blox.com/sites/default/files/2022-06/u-centersetup_v22.05.zip?_ga=2.166793531.441583464.1657687777-673334558.1657687777),  [User Guide](https://content.u-blox.com/sites/default/files/u-center_Userguide_UBX-13005250.pdf)

<iframe width="640" height="360" src="https://www.youtube.com/embed/n8PUyOtiGKo" title="Neo-M8P RTK setup and demo (courtesy u-blox)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Set up Ublox Base and Rover Devices
**Blog:** [Autonomous Agri-robot Control System](https://hackaday.io/project/90057/instructions?page=1)
![](https://cdn.hackaday.io/images/9986121523093351759.jpg)
* For an initial test, use the quick 2 minute 'survey in' file: [Ublox_Base_20minutes.txt](https://cdn.hackaday.io/files/900573852998688/Ublox%20Base%20%202%20minutes.txt)
* For accurate, repeatable, results use the 24 hour version - be warned  - it takes 24 hours before you can use the devices! : [Ublox Base 20hours.txt](https://cdn.hackaday.io/files/900573852998688/Ublox%20Base%20%2024%20hours%20.txt)
* The Rover uses the same config file whatever: [Ublox Rover.txt](https://cdn.hackaday.io/files/900573852998688/Ublox%20Rover.txt)

---
### [RTK M8P Positioning Solutions](https://drotek.gitbook.io/rtk-positioning-solutions/)
* [Drotek RTK GNSS modules using NEO-M8P](https://drotek.gitbook.io/rtk-positioning-solutions/)
* [Configuring the base manually](https://drotek.gitbook.io/rtk-positioning-solutions/the-rtk-base/configuring-the-base-manually)
* [Configuring the rover manually](https://drotek.gitbook.io/rtk-positioning-solutions/the-rtk-rover/untitled)
* [The Telemetry system (MAVLink)](https://drotek.gitbook.io/rtk-positioning-solutions/the-telemetry-system)
![](https://2089968121-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LYSZ2RX-sZFfz9kI3R4%2F-LYh07Z09W8PTH41W143%2F-LYh0DjQWtnhQYRZfzks%2Ftelemetry-drotek-doc.png?alt=media&token=ac6301bb-830e-48cb-86a7-acb2be660aa9)

---
### SparkFun GPS-RTK board - NEO-M8P-2
* [GPS-RTK Hookup Guide](https://learn.sparkfun.com/tutorials/gps-rtk-hookup-guide/all)
![](https://cdn.sparkfun.com/assets/learn_tutorials/8/1/4/SparkFun_GPS_GNSS-RTK_Evaluation_Board.jpg)

* [SparkFun Ublox Arduino Library](https://github.com/sparkfun/SparkFun_Ublox_Arduino_Library)
  - **Example1**: Read NMEA sentences over I2C using u-blox module SAM-M8Q, NEO-M8P, etc
  - **Example2**: Parse NMEA sentences using MicroNMEA library. This example also demonstrates how to overwrite the processNMEA function so that you can direct the incoming NMEA characters from the u-blox module to any library, display, radio, etc that you prefer.
  - **Example3**: Get latitude, longitude, altitude, and satellites in view (SIV). This example also demonstrates how to turn off NMEA messages being sent out of the I2C port. You’ll still see NMEA on UART1 and USB, but not on I2C. Using only UBX binary messages helps reduce I2C traffic and is a much lighter weight protocol.
  - **Example4**: Displays what type of a fix you have the two most common being none and a full 3D fix. This sketch also shows how to find out if you have an RTK fix and what type (floating vs. fixed).
  - **Example5**: Shows how to get the current speed, heading, and dilution of precision.
  - **Example6**: Demonstrates how to increase the output rate from the default 1 per second to many per second; up to 30Hz on some modules!
  - **Example7**: Older modules like the SAM-M8Q utilize an older protocol (version 18) whereas the newer modules like the ZED-F9P depricate some commands using the latest protocol (version 27). This sketch shows how to query the module to get the protocol version.
  - **Example8**: u-blox modules use I2C address 0x42 but this is configurable via software. This sketch will allow you to change the module’s I2C address.
  - **Example9**: Altitude is not a simple measurement. This sketch shows how to get both the ellipsoid based altitude and the MSL (mean sea level) based altitude readings.
  - Example10: Sometimes you just need to do a hard reset of the hardware. This sketch shows how to set your u-blox module back to factory default settings.
  - **NEO-M8P**: Examples specific for the NEO-M8P.
  - **NEO-M8P Example1**: Send UBX binary commands to enable RTCM sentences on U-blox NEO-M8P-2 module. This example is one of the steps required to setup the NEO-M8P as a base station. For more information have a look at the u-blox manual for setting up an RTK link.
  - **NEO-M8P Example2**: This example extends the previous example sending all the commands to the NEO-M8P-2 to have it operate as a base. Additionally the processRTCM function is exposed. This allows the user to overwrite the function to direct the RTCM bytes to whatever connection the user would like (radio, serial, etc).
  - NEO-M8P Example3: This is the same example as NEO-M8P's Example2. However, the data is sent to a serial LCD via I2C.
  - **ZED-F9P**: Examples specific for the ZED-F9P.
  - **ZED-F9P Example1**: This module is capable of high precision solutions. This sketch shows how to inspect the accuracy of the solution. It’s fun to watch our location accuracy drop into the millimeter scale.
  - **ZED-F9P Example2**: The ZED-F9P uses a new u-blox configuration system of VALGET/VALSET/VALDEL. This sketch demonstrates the basics of these methods.
  - **ZED-F9P Example3**: Setting up the ZED-F9P as a base station and outputting RTCM data.
  - **ZED-F9P Example4**: This is the same example as ZED-F9P's Example3. However, the data is sent to a serial LCD via I2C.

* There are only three steps to initiating a base station:
  - Enable Survey-In mode for 5 minutes (300 seconds)
  - Enable RTCM output messages
  - Begin transmitting the RTCM packets over the backhaul of choice

* If you have a ‘rover’ in the field in need of correction data you’ll need to get the RTCM bytes to the rover. The SparkFun u-blox library automatically detects the difference between NMEA sentences and RTCM data. The processRTCM() function allows you to ‘pipe’ just the RTCM correction data to the channel of your choice. Once the base station has completed the survey and has the RTCM messages enabled, your custom processRTCM() function can pass each byte to any number of channels:
  - A wireless system such as LoRa or Cellular
  - Posting the bytes over the internet using WiFi or wired ethernet over an **Ntrip** caster 
  - Over a wired solution such as RS485
  - The power of the **processRTCM()** function is that it doesn’t care; it presents the user with the incoming byte and is agnostic about the back channel.
* [EMLID NTRIP CASTER](https://emlid.com/ntrip-caster/): Pass corrections between your RTK GNSS receivers over the Internet
  
---
### [Ardupilot - Here+ RTK GPS](https://ardupilot.org/copter/docs/common-here-plus-gps.html?highlight=m8p)
![](https://ardupilot.org/copter/_images/here-plus-gps.png)
[Here 3 & Here+ RTK Base (M8P) Combo](https://irlock.com/products/here-3-here-rtk-base-m8p-combo)
![](https://cdn.shopify.com/s/files/1/0599/7905/products/mainpic_large.png?v=1657414426)

---
### [Integration of ublox M8P RTK in Ardupilot](https://discuss.ardupilot.org/t/integration-of-ublox-m8p-rtk-in-ardupilot/12384/5)
![](https://discuss.ardupilot.org/uploads/default/optimized/2X/3/3346843bb40721f4914606d5c89f801a6fd947ea_2_662x500.png)

---
## Bad GPS reception

### Kalman Filter
**Paper:** [A Kalman filter approach to reduce position error for pedestrian applicationsin areas of bad GPS reception](https://www.diva-portal.org/smash/get/diva2:743775/FULLTEXT01.pdf)<br>
![](https://github.com/rkuo2000/Robotics/blob/main/images/Kalman_Filter_approach_to_reduce_position_error.png?raw=true)

<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*
