---
layout: post
title: 四足機器人簡介
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Mini Pupper, SpotMicro, Xiaomi CyberDog, ...etc.

---
## 四足機器人介紹

### Petoi Bittle (using 8 servo)
<iframe width="854" height="480" src="https://www.youtube.com/embed/MEhJzbhxm8A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### PIPPY
[樹莓派仿生機器狗](https://www.ruten.com.tw/item/show?22112277216575)<br>
![](https://gd3.alicdn.com/imgextra/i1/2566773369/O1CN01kJJE3v1al30nQ9vf1_!!2566773369.jpg)

### BeeDog
![](https://ae01.alicdn.com/kf/Hdd485ee7a9a449f38e15a31a81d6636d9.jpg)

#### SpotMicro
<iframe width="854" height="480" src="https://www.youtube.com/embed/6mbWF_FTK-o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="854" height="480" src="https://www.youtube.com/embed/S-uzWG9Z-5E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [Unitree-Go1](https://www.unitree.com/products/go1/)
<iframe width="854" height="480" src="https://www.youtube.com/embed/a3-JVELVkfc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [Xiaomi CyberDog](https://www.mi.com/cyberdog)
<iframe width="854" height="480" src="https://www.youtube.com/embed/a1Jo2MXVUOg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
> 产品名称：CyberDog 仿生四足机器人 <br />
> 站立：长度：771mm, 宽度：355mm, 高度：400mm, 趴下：长度：807mm <br />
> 宽度：406mm, 高度：206mm <br />
> 整机重量（含电池）：14kg <br />
> 自由度：整机12，单腿3 <br />
> Ubuntu 18.04+ROS 2 <br />

> 支持步态：恢复站立丨姿态展示丨缓慢趴下丨缓跑丨小跑丨奔跑丨跳跑丨跳跃 <br />
> 更多能力：倒地恢复丨打滚丨握手丨跳舞丨转圈丨作揖丨坐下 <br />
> 最大负载：3kg <br />
> 动态平衡：支持 <br />
> 运动速度：MAX 3.2m/s* <br />
> 倒地恢复：支持 <br />
> 摔倒保护：支持 <br />
*实验室测得整机最大行走速度为3.2m/s，最大安全行走速度为1.6m/s  <br />

---
## 3D-Printed Robot Dog
### Mini Pupper
[Github](https://github.com/mangdangroboticsclub/QuadrupedRobot)<br>
[PLA.PupperMini.3DPrint](https://drive.google.com/file/d/1T_J6pcALxuLAoklKPrTxZPnOd6V5lY8z/view)<br>
[Hackaday.io](https://hackaday.io/project/180171-mini-pupper-open-sourceros-robot-dog-kit)<br>
<iframe width="771" height="434" src="https://www.youtube.com/embed/rLl6KXRb_9k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [SuperMicro V2](https://pinshape.com/items/59662-3d-printed-spotmicro-v2)<br>
[SpotMicro V2 STL](https://3dmixers.com/m/download/65285)<br>
![](https://assets.pinshape.com/uploads/image/file/287705/container_spotmicro-v2-3d-printing-287705.jpg)
<iframe width="771" height="434" src="https://www.youtube.com/embed/LqLittumdvQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Servo Horn Tester**<br>
To avoid spending countless hours printing just to find out this design doesn't fit your servos, I'd recommend printing the servo tester. It prints quite fast and you ensure every other print will work with your hardware.<br>

* 1 x ServoHornTester.stl

**Body**<br>
* 1 x Chassis_Baseplate_v2.0.stl (compatible with SpotMicro v1.0)
* 2 x Chassis_Side_v2.0.stl (compatible with SpotMicro v1.0)
* 1 x F_I_Shoulder_v2.0.stl
* 1 x F_O_Shoulder_v2.0.stl
* 1 x B_I_Shoulder_v2.0.stl
* 1 x B_O_Shoulder_v2.0.stl

**Legs**<br>

* 2 x L_HindLimb_v2.0.stl
* 2 x L_MidLimb_v2.0.stl
* 2 x L_Wrist_v2.0.stl
* 2 x L_MidLimbCover_v2.0.stl (compatible with SpotMicro v1.0)
* 2 x R_HindLimb_v2.0.stl
* 2 x R_MidLimb_v2.0.stl
* 2 x R_Wrist_v2.0.stl
* 2 x R_MidLimbCover_v2.0.stl
* 4 x Foot_v2.0.stl (Better if printed in TPU or any elastic material)

**Covers**<br>
* 1 x Cover_Top_v2.0.stl
* 1 x Cover_Bottom_v2.0.stl
* 1 x Head_RPiCam_v2.0.stl
* 1 x Butt_Empty_v2.0.stl

---
### Open Dynamic Robot Initiative
[Mechanics](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware/tree/master/mechanics)<br>
**Quadruped Robot 12dof**<br>
![](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware/raw/master/mechanics/quadruped_robot_12dof_v1/images/solo12_8.jpg?raw=true)
**Biped Robot 6dof**<br>
![](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware/raw/master/mechanics/biped_6dof_v1/images/biped_cad_5.png?raw=true)

---
## 四足機器人運動技巧之學習訓練
### Learning Agile Robotic Locomotion Skills by Imitating Animals
**[Github](https://github.com/google-research/motion_imitation)** <br />
**[Paper](https://xbpeng.github.io/projects/Robotic_Imitation/index.html)** <br />

<iframe width="854" height="480" src="https://www.youtube.com/embed/lKYh6uuCwRY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

