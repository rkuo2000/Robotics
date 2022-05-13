---
layout: post
title: 視覺慣性導航系統
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to Datasets VIO, OpenVINS, VINS-Mono, VINS-Fusion, cm-Level GPS positioning, and (EuRoC-MAV, TUM Visual-Inertial Dataset, UZH-FPV Drone Racing Dataset, KAIST Urban Dataset, KAIST VIO Dataset, KITTI Vision Benchmark suite, Visual Odometry / SLAM Evaluation).

---
## [Visual-Inertial odometry (VIO)](https://www.ifi.uzh.ch/en/rpg/research/research_vo.html)
Visual-Inertial odometry (VIO) is the process of estimating the state (pose and velocity) of an agent (e.g., an aerial robot) by using only the input of one or more cameras plus one or more Inertial Measurement Units (IMUs) attached to it. VIO is the only viable alternative to GPS and lidar-based odometry to achieve accurate state estimation. Since both cameras and IMUs are very cheap, these sensor types are ubiquitous in all today's aerial robots.

**[Visual-Inertial Odometry of Aerial Robots](https://arxiv.org/pdf/1906.03289.pdf)**<br>
![](https://www.ifi.uzh.ch/ifi/dam/jcr:f42530e2-1c13-41b0-a7cf-2a48191ee72f/Encyclopedia19VIO_Scaramuzza.2019-06-07-21-33-10.png)

---
### [Probabilistic, Continuous-Time Trajectory Evaluation for SLAM](https://www.ifi.uzh.ch/dam/jcr:a7562b85-846d-40f2-b122-55ca36b89f9c/WICRA19_Zhang.pdf)
![](https://www.ifi.uzh.ch/ifi/dam/jcr:13929031-defb-46d2-8c69-ca395cc11c26/WICRA19_Zhang_full.2019-05-29-11-38-40.png)

---
### [Fisher Information Field for Active Visual Localization](https://www.ifi.uzh.ch/dam/jcr:5a26a3b4-ce01-4647-8cf6-f6a24e579a85/ICRA19_Zhang.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/q3YqIyaFUVE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [A Tutorial on Quantitative Trajectory Evaluation for Visual(-Inertial) Odometry](https://www.ifi.uzh.ch/dam/jcr:89d3db14-37b1-431d-94c3-8be9f37466d3/IROS18_Zhang.pdf)
  - [PPT](https://www.ifi.uzh.ch/dam/jcr:fd6089ce-2414-4a4f-98ca-8a48ad318990/IROS18_Zhang.pptx)
  - [VO/VIO Evaluation Toolbox](https://github.com/uzh-rpg/rpg_trajectory_evaluation)
![](https://www.ifi.uzh.ch/ifi/dam/jcr:49c72c35-54aa-4209-8418-8e0f967660f0/IROS18_Zhang.2018-10-08-18-08-14.png)

---
### On the Comparison of Gauge Freedom Handling in Optimization-based Visual-Inertial State Estimation
* [On the Comparison of Gauge Freedom Handling in Optimization-based Visual-Inertial State Estimation](https://www.ifi.uzh.ch/dam/jcr:3ef325f5-aa80-44e1-9d37-1ab7218ff922/RAL18_Zhang.pdf)
  - [PPT](https://www.ifi.uzh.ch/dam/jcr:f77ffa5e-3496-4b7e-97df-1ff7bb572fd1/RAL18_Zhang.pptx)
  - [Code](https://github.com/uzh-rpg/rpg_vi_cov_transformation)
  
![](https://www.ifi.uzh.ch/ifi/dam/jcr:cb4f9448-8105-4ba9-ad2e-75acc709a85f/RAL18_Zhang_teaser.png)

---
### [Active Exposure Control for Robust Visual Odometry in High Dynamic Range (HDR) Environments](https://www.ifi.uzh.ch/dam/jcr:cc5c71f1-3491-4c7e-9490-bb16278aa75e/ICRA17_Zhang_updated.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/TKJ8vknIXbM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### IMU Preintegration on Manifold for Efficient Visual-Inertial Maximum-a-Posteriori Estimation
* [On-Manifold Preintegration for Real-Time Visual-Inertial Odometry](https://www.ifi.uzh.ch/dam/jcr:67a6caa8-84e8-4f9b-9744-aefaec68d308/TRO16_forster.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/CsJkci5lfco" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* [IMU Preintegration on Manifold for Efficient Visual-Inertial Maximum-a-Posteriori Estimation](https://www.ifi.uzh.ch/dam/jcr:b8afbc75-3bcf-4896-9611-cdd0bddd2509/RSS15_Forster.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/CsJkci5lfco" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### REMODE
[REMODE: Probabilistic, Monocular Dense Reconstruction in Real Time](https://www.ifi.uzh.ch/dam/jcr:7edf1f0c-aaa1-470f-930a-f77faec4a2f0/ICRA14_Pizzoli.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/gr00Bf0AP1k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### SVO: Fast Semi-Direct Monocular Visual Odometry
[SVO: Semi-Direct Visual Odometry for Monocular and Multi-Camera Systems](http://rpg.ifi.uzh.ch/docs/TRO16_Forster-SVO.pdf)
<iframe width="996" height="560" src="https://www.youtube.com/embed/2YnIMfw6bJY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### SVO 2.0 Semi-Direct Visual Odometry
[SVO 2.0: Semi-Direct Visual Odometry for Monocular and Multi-Camera Systems](https://rpg.ifi.uzh.ch/docs/TRO17_Forster-SVO.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/hR8uq1RTUfA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**[SVO Pro](https://github.com/uzh-rpg/rpg_svo_pro_open)**<br>
![](https://github.com/uzh-rpg/rpg_svo_pro_open/raw/master/doc/images/v102_gm.gif)

---
### 1-point RANSAC
Given a car equipped with an omnidirectional camera, the motion of the vehicle can be purely recovered from salient features tracked over time. We propose the 1-Point RANSAC algorithm which runs at 800 Hz on a normal laptop. 
![](https://www.ifi.uzh.ch/dam/jcr:46cb5ecd-4a84-4c5a-8ef0-dd7709bf32b2/teaser_1.2017-01-05-22-40-09.gif)
<iframe width="826" height="620" src="https://www.youtube.com/embed/t7uKWZtUjCE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Visual-LiDar Odometry
* [Visual-lidar Odometry and Mapping: Low-drift, Robust, and Fast](https://frc.ri.cmu.edu/~zhangji/publications/ICRA_2015.pdf)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/Visual-lidar_Odometry_and_Mapping.png?raw=true)
<iframe width="1280" height="720" src="https://www.youtube.com/embed/-6cwhPMAap8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [Visual-Inertial Odometry Benchmarking](https://www.ifi.uzh.ch/ifi/rpg/docs/ICRA18_Delmerico.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/ymI3FmwU9AY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Prerequisites for VINS installation
* check if Swap is on<br>
`swapon -s`<br>
* if not add Swap space
```
sudo mkdir -p /var/cache/swap/
sudo dd if=/dev/zero of=/var/cache/swap/swap0 bs=64M count=64 # swap=64MB*64=4096MB
sudo chmod 0600 /var/cache/swap/swap0
sudo mkswap /var/cache/swap/swap0
sudo swapon /var/cache/swap/swap0
swapon -s
```

[Installation Guide](https://docs.openvins.com/gs-installing.html)<br>
* [ROS 1 Noetic (uses OpenCV 4.2)](http://wiki.ros.org/noetic/Installation/Ubuntu)<br>
* [ROS 2 Galactic (uses OpenCV 4.2)](https://docs.ros.org/en/galactic/)<br>

### [Ceres Solver 2.1.0 Installation](http://ceres-solver.org/installation.html) (optional)
```
sudo apt-get install cmake 
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libeigen3-dev
sudo apt-get install libsuitesparse-dev
```
```
wget http://ceres-solver.org/ceres-solver-2.1.0.tar.gz
tar zxf ceres-solver-2.1.0.tar.gz
mkdir ceres-bin
cd ceres-bin
cmake ../ceres-solver-2.1.0
make -j4
sudo make install
```

---
### ROVIO
[Iterated extended Kalman filter based visual-inertial odometry using direct photometric feedback](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/263423/ROVIO.pdf?sequence=1&isAllowed=y)<br>
![](https://d3i71xaburhd42.cloudfront.net/6b8ac6a81515f023f45e7f2ffa6a18177682d8be/7-Figure3-1.png)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/IEKF-based-VIO_flow_graph_of_filter_framework.png?raw=true)
Flow graph of the filter framework. <br>
The processing of the inertial (ω˜ , f˜) and visual (I) measurements (red terms) is tightly embedded in the IEKF framework.<br>
The filter state x and covariance P are alternatively processed by an IMU-based prediction step and a vision-based update step.<br> 
Most of the visual information is processed as part of the iterative update step (grey block). <br>
The order and dependencies of the image processing sub-steps are also illustrated and the numbers represent the references to the corresponding sections.<br>

---
### OKVIS 
[OKVIS: Keyframe-Based Visual-Inertial SLAM using Nonlinear Optimization](http://www.roboticsproceedings.org/rss09/p37.pdf)<br>
<iframe width="1004" height="565" src="https://www.youtube.com/embed/TbKEPA2_-m4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**[Github](https://github.com/ethz-asl/okvis_ros)**<br>

---
### [OpenINVS](https://github.com/rpng/open_vins)
**paper:** [OpenVINS: A Research Platform for Visual-Inertial Estimation](http://udel.edu/~pgeneva/downloads/papers/c10.pdf)<br>
The OpenVINS project houses some core computer vision code along with a state-of-the art filter-based visual-inertial estimator. The core filter is an [Extended Kalman filter](https://en.wikipedia.org/wiki/Extended_Kalman_filter) which fuses inertial information with sparse visual feature tracks. These visual feature tracks are fused leveraging the [Multi-State Constraint Kalman Filter (MSCKF)](https://www-users.cse.umn.edu/~stergios/papers/ICRA07-MSCKF.pdf) sliding window formulation which allows for 3D features to update the state estimate without directly estimating the feature states in the filter. 

* [Documentation](https://docs.openvins.com/)<br>
* [Getting started guide](https://docs.openvins.com/getting-started.html)
```
mkdir -p ~/catkin_openvins/src/
cd ~/catkin_openvins/src/
git clone https://github.com/rpng/open_vins
cd ..
```
  - For ROS1
  ```
  catkin build
  ```
  - For ROS2
  ```
  colcon build
  colcon build --event-handlers console_cohesion+ --packages-select ov_core ov_init ov_msckf ov_eval # ROS2 with verbose output
  ```
**Demo Videos:**<br>
<iframe width="370" height="208" src="https://www.youtube.com/embed/KCX51GvYGss" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/Lc7VQHngSuQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/vaia7iPaRW8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/MCzTF9ye2zw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/eSQLWcNrx_I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/187AXuuGNNw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/oUoLlrFryk0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/ExPIGwORm4E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="370" height="208" src="https://www.youtube.com/embed/lXHl-qgLGl8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
* [Publications](https://sites.udel.edu/robot/publications/)

  - [MIMC-VINS: A Versatile and Resilient Multi-IMU Multi-Camera Visual-Inertial Navigation System](https://arxiv.org/abs/2006.15699)<br>
  <iframe width="789" height="444" src="https://www.youtube.com/embed/my1IjdJ4irY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

  - [Multi-IMU VIO: Sensor-Failure-Resilient Multi-IMU Visual-Inertial Navigation](https://udel.edu/~pgeneva/downloads/papers/c06.pdf)<br>
  <iframe width="789" height="444" src="https://www.youtube.com/embed/TqbzqLgnIZc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

--- 
### [VINS-Mobile](https://github.com/HKUST-Aerial-Robotics/VINS-Mobile)
[The Integration of GPS/BDS Real-Time Kinematic Positioning and Visual–Inertial Odometry Based on Smartphones](https://mdpi-res.com/d_attachment/ijgi/ijgi-10-00699/article_deploy/ijgi-10-00699-v2.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/0mTXnIfFisI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono)
[VINS-Mono: A Robust and Versatile Monocular Visual-Inertial State Estimator](https://arxiv.org/pdf/1708.03852.pdf)<br>
<iframe width="863" height="411" src="https://www.youtube.com/embed/eINyJHB34uU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="347" height="206" src="https://www.youtube.com/embed/mv_9snb_bKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="347" height="206" src="https://www.youtube.com/embed/g_wN0Nt0VAU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="347" height="206" src="https://www.youtube.com/embed/I4txdvGhT6I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
![](https://www.researchgate.net/publication/355247417/figure/fig2/AS:1079250023133186@1634324665587/The-framework-of-VINS-mono.png)

---
[VINS-Mono代碼解析——狀態估計器流程](https://www.cxymm.net/article/qq_43247439/107312670)<br>

![](https://img-blog.csdnimg.cn/20190222143043441.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODM5MjIy,size_16,color_FFFFFF,t_70)

**vins_estimator**<br>
* factor：
  - imu_factor.h：IMU残差、雅可比
  - intergration_base.h：IMU预积分
  - marginalization.cpp/.h：边缘化
  - pose_local_parameterization.cpp/.h：局部参数化
  - projection_factor.cpp/.h：视觉残差
* initial：
  - initial_alignment.cpp/.h：视觉和IMU校准(陀螺仪偏置、尺度、重力加速度和速度)
  - initial_ex_rotation.cpp/.h：相机和IMU外参标定
  - initial_sfm.cpp/.h：纯视觉SFM、三角化、PNP
  - solve_5pts.cpp/.h：5点法求基本矩阵得到Rt
* utility：
  - CameraPoseVisualization.cpp/.h：相机位姿可视化
  - tic_toc.h：记录时间
  - utility.cpp/.h：各种四元数、矩阵转换
  - visualization.cpp/.h：各种数据发布
  - estimator.cpp/.h：紧耦合的VIO状态估计器实现
  - estimator_node.cpp：ROS 节点函数，回调函数
  - feature_manager.cpp/.h：特征点管理，三角化，关键帧等
  - parameters.cpp/.h：读取参数
  
---
### [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)
[A General Optimization-based Framework for Local Odometry Estimation with Multiple Sensors](https://arxiv.org/pdf/1901.03638.pdf)

**[Code](https://github.com/rkuo2000/VINS-Fusion)**<br>

**VI-Car**<br>
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/raw/master/support_files/image/car_gif.gif)

**EuRoC-MAV**<br>
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/raw/master/support_files/image/euroc.gif)
  
**KITTI**<br>
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/raw/master/support_files/image/kitti.gif)
* KITTI Odometry (Stereo)
  - Download [KITTI Odometry dataset](http://www.cvlibs.net/datasets/kitti/eval_odometry.php) to YOUR_DATASET_FOLDER. 
  - `roslaunch vins vins_rviz.launch`
  - (optional) `rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/kitti_odom/kitti_config00-02.yaml`
  - `rosrun vins kitti_odom_test ~/catkin_ws/src/VINS-Fusion/config/kitti_odom/kitti_config00-02.yaml YOUR_DATASET_FOLDER/sequences/00/`

* KITTI GPS Fusion (Stereo + GPS)
  - Download [KITTI raw dataset](http://www.cvlibs.net/datasets/kitti/raw_data.php) to YOUR_DATASET_FOLDER. 
 Take [2011_10_03_drive_0027_synced](https://s3.eu-central-1.amazonaws.com/avg-kitti/raw_data/2011_10_03_drive_0027/2011_10_03_drive_0027_sync.zip) for example.
  - `roslaunch vins vins_rviz.launch`
  - `rosrun vins kitti_gps_test ~/catkin_ws/src/VINS-Fusion/config/kitti_raw/kitti_10_03_config.yaml YOUR_DATASET_FOLDER/2011_10_03_drive_0027_sync/`
  - `rosrun global_fusion global_fusion_node`
  
* [Recalibrating the KITTI Dataset Camera Setup for Improved Odometry Accuracy](https://arxiv.org/pdf/2109.03462.pdf)
  ![](https://xuwuzhou.top/images/%E8%AE%BA%E6%96%8752%E5%9B%BE%E7%89%873.png) 
 
---
### VINS-Fusion 代碼解析
* [VINS Fusion 笔记](https://scm_mos.gitlab.io/slam/VINS-FUSION/)

* [浅谈VINS中的global fusion节点](https://zhuanlan.zhihu.com/p/75492883)

* [VINS 论文推导及代码解析（一）](https://mp.weixin.qq.com/s/opInITC_BDWz12j1_nUseA)
* [VINS 论文推导及代码解析（二）](https://mp.weixin.qq.com/s/9twYJMOE8oydAzqND0UmFw)
* [VINS 论文推导及代码解析（三）](https://mp.weixin.qq.com/s/xumEhRziRCpnAW36Utuo4A)
* [VINS 论文推导及代码解析（四）](https://mp.weixin.qq.com/s/edAwdBxV-j2bgfpnxxQSzA)

---
### Improved VINS-Mono
[Robust Visual-Inertial Navigation System for Low Precision Sensors under Indoor and Outdoor Environments](https://www.researchgate.net/publication/349465261_Robust_Visual-Inertial_Navigation_System_for_Low_Precision_Sensors_under_Indoor_and_Outdoor_Environments)
![](https://www.researchgate.net/publication/349465261/figure/fig1/AS:993333975474176@1613840683010/The-improved-visual-inertial-navigation-system-VINS-mono-system-architecture-framework.png)
![](https://www.researchgate.net/publication/349465261/figure/tbl2/AS:993333975449602@1613840683457/Trajectory-accuracy-of-the-improved-VINS-mono-EuRoc-Dataset.png)

---
### [PL-VIO](https://github.com/HeYijia/PL-VIO)
[PL-VIO: Tightly-Coupled Monocular Visual–Inertial Odometry Using Point and Line Features](https://www.semanticscholar.org/paper/PL-VIO%3A-Tightly-Coupled-Monocular-Visual%E2%80%93Inertial-He-Zhao/6356897ee4a51a1f9de04a8ab959afd97af7f63e)
<table>
<tr>
<td><img src="https://d3i71xaburhd42.cloudfront.net/6356897ee4a51a1f9de04a8ab959afd97af7f63e/4-Figure1-1.png"></td>
<td><img src="https://d3i71xaburhd42.cloudfront.net/6356897ee4a51a1f9de04a8ab959afd97af7f63e/6-Figure2-1.png"></td>
</tr>
</table>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PL-VIO_benchmark.png?raw=true)
**[Code](https://github.com/rkuo2000/PL-VIO)**<br>
![](https://github.com/rkuo2000/PL-VIO/raw/master/doc/image/plvio.gif)

---
### PL-VINS
[PL-VINS: Real-Time Monocular Visual-Inertial SLAM with Point and Line Features](https://arxiv.org/abs/2009.07462)<br>
<iframe width="740" height="416" src="https://www.youtube.com/embed/MPf6HufbgdE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
![](https://d3i71xaburhd42.cloudfront.net/148eebf5cddccf37891074d118945de0df2328a7/1-Figure1-1.png)
![](https://d3i71xaburhd42.cloudfront.net/148eebf5cddccf37891074d118945de0df2328a7/3-Figure2-1.png)
*The Blue rectangles represent the differences from VINS-Mono*<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PL-VINS_benchmark.png?raw=true)
**[Code](https://github.com/rkuo2000/PL-VINS)**<br>
![](https://github.com/cnqiangfu/PL-VINS/raw/master/support_files/plvins-vinsmono.png)
<span style="color: red">*The build took ~37 hours on i7-920 @2.67GHz !!!*</span><br>
**MH_01_easy**<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PL-VINS_MH_01_easy.png?raw=true)
**MH_05_difficult**<br>
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PL-VINS_MH_05_difficult.png?raw=true)

---
### IPL-VIO
[Improved Point–Line Visual–Inertial Odometry System Using Helmert Variance Component Estimation](https://www.mdpi.com/2072-4292/12/18/2901/htm)
![](https://www.mdpi.com/remotesensing/remotesensing-12-02901/article_deploy/html/images/remotesensing-12-02901-g001.png)
![](https://www.mdpi.com/remotesensing/remotesensing-12-02901/article_deploy/html/images/remotesensing-12-02901-g006a.png)
![](https://www.mdpi.com/remotesensing/remotesensing-12-02901/article_deploy/html/images/remotesensing-12-02901-g006b.png)
Figure 6 Comparision of the matching effect between line binary descriptors(LBD) matching method and improved mathcing method on the MH_02_easy dataset.
Images(a,b) are LBD descriptor matching scenes - the line of the same color is the corresponding matching line; (c,d) are the matching scenes of the improved matching method, and the line of the same color is the corresponding matching line.
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/IPL-VIO_benchmark.png?raw=true)

---
### PLS-VIO
[Leveraging Structural Information to Improve Point Line Visual-Inertial Odometry](https://arxiv.org/pdf/2105.04064.pdf)
![](https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/b770639b633bb6469a13805ea28ba6626dc682ce/1-Figure1-1.png)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/PLS-VIO_benchmark.png?raw=true)
**[Code](https://github.com/rkuo2000/Structural-and-Non-structural-line)**<br>
![](https://github.com/rkuo2000/Structural-and-Non-structural-line/raw/master/bin/demo/simulate_line.gif)

---
### RK-VIF
[An improved SLAM based on RK-VIF: Vision and inertial information fusion via Runge-Kutta method](https://www.sciencedirect.com/science/article/pii/S2214914721001938)

1. Visual-inertial information fusion framework
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr1.jpg)

2. The process of PROSAC algorithm<br>
  The [PROSAC](https://www.researchgate.net/publication/327114888_An_efficient_RANSAC_hypothesis_evaluation_using_sufficient_statistics_for_RGB-D_pose_estimation) is based on the assumption that “the points with good quality are more likely to be interior points”.<br>
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr2.jpg)

3. This paper uses the Runge-Kutta method to discretize the IMU motion formula to improve the pre-integration accuracy. The basic idea of the Runge-Kutta method is to estimate the derivatives of multiple points in the integration interval, take the weighted average of these derivatives to obtain the average derivative, and then use the average derivative to estimate the result at the end of the integration interval. 
  The formula of the fourth-order Runge-Kutta algorithm is as follows:
  ![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/Runge-Kutta_algorithm_formula.png?raw=true) 
  
4. Sensor frequency
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr3.jpg)

5. VINS state and constraints
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr4.jpg)

6. Sliding window optimization range
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr5.jpg)

7. Loop detection process
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr6.jpg)
  After the system successfully detects the loop, it can establish the constraint relationship between the two frames through feature matching. Firstly, we need to fuse the map points matched by the loop and eliminate redundant map points. Then calculate the relative pose between the two keyframes according to Perspective-N-Point (PnP) algorithm, and correct the current keyframe's pose. In addition, other keyframes in the loop also have different degrees of accumulated error and need to be globally optimized.

8. Globally optimized pose
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr7.jpg)

9. Dataset experiment
  ![](https://ars.els-cdn.com/content/image/1-s2.0-S2214914721001938-gr9.jpg)

The RMSE in EuRoC Dataset (unit: m)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/RK-VIF_benchmark.png?raw=true)

--- 
## GPS-VIO

### [The Integration of GPS-BDS Real-Time Kinematic Positioning and Visual–Inertial Odometry Based on Smartphones](https://www.mdpi.com/2220-9964/10/10/699/pdf)**
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g001.png)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g002.png)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g005.png)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g006.png)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g007-550.jpg)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g008-550.jpg)
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g015-550.jpg)

---
### [Tightly-coupled Fusion of Global Positional Measurements in Optimization-based Visual-Inertial Odometry](https://arxiv.org/abs/2003.04159)
<table>
<tr>
<td><img src="https://d3i71xaburhd42.cloudfront.net/8a83dbab2609a1d204cf431fa4b93aa2b4148e8d/1-Figure1-1.png"></td>
<td><img src="https://d3i71xaburhd42.cloudfront.net/8a83dbab2609a1d204cf431fa4b93aa2b4148e8d/2-Figure2-1.png"></td>
</tr>
</table>
![](https://d3i71xaburhd42.cloudfront.net/8a83dbab2609a1d204cf431fa4b93aa2b4148e8d/6-Figure4-1.png)

---
### [Tightly Coupled Optimization-based GPS-Visual-Inertial Odometry with Online Calibration and Initialization](https://arxiv.org/abs/2203.02677)
<table>
<tr>
<td><img src="https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/b76f11bfab2e84e42f4d4921eed35af76687e40b/1-Figure1-1.png"></td>
<td><img src="https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/b76f11bfab2e84e42f4d4921eed35af76687e40b/3-Figure3-1.png"></td>
</tr>
</table>


---
## cm-Level GPS positioning
![](https://img.ruten.com.tw/s1/9/58/23/21006055090211_380.jpg)
<iframe width="826" height="465" src="https://www.youtube.com/embed/28_YpdN8Thw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**[RTK Networks – What, Why, Where?](https://www.gps.gov/cgsic/meetings/2009/gakstatter1.pdf)**<br>

**[Network Real Time Kinematic (NRTK) Positioning – Description, Architectures and Performances](https://www.researchgate.net/profile/Marco-Piras-2/publication/282339192_Network_Real_Time_Kinematic_NRTK_Positioning_-_Description_Architectures_and_Performances/links/572f487b08aeb1c73d13a0c2/Network-Real-Time-Kinematic-NRTK-Positioning-Description-Architectures-and-Performances.pdf)**<br>

---
## [Datasets](https://docs.openvins.com/gs-datasets.html)

### [EuRoC MAV Dataset](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets)
The ETH ASL EuRoC MAV dataset is one of the most used datasets in the visual-inertial / simultaneous localization and mapping (SLAM) research literature. 
<table>
<tr>
<td><img src="https://projects.asl.ethz.ch/datasets/lib/exe/fetch.php?w=230&tok=f969d3&media=overview_ml.jpg"></td>
<td><img src="https://projects.asl.ethz.ch/datasets/lib/exe/fetch.php?w=320&tok=2b9d8d&media=vicon_pointcloud_training_crop.png"></td>
</tr>
</table>
**Platform and Sensors**<br>
![](https://projects.asl.ethz.ch/datasets/lib/exe/fetch.php?w=400&tok=1dbdef&media=platform.jpg)
![](https://projects.asl.ethz.ch/datasets/lib/exe/fetch.php?w=210&tok=3d9fd6&media=front_side_gray.jpg)

---
### [TUM Visual-Inertial Dataset](https://vision.in.tum.de/data/datasets/visual-inertial-dataset)
![](https://vision.in.tum.de/_media/data/datasets/vi-dataset/thumbs.png?w=1000&tok=4756bb)

---
### [RPNG OpenVINS Dataset](https://docs.openvins.com/gs-datasets.html#gs-data-rpng)
* ArUco Datasets:
  - Core visual-inertial sensor is the [VI-Sensor](https://furgalep.github.io/bib/nikolic_icra14.pdf)
  - Stereo global shutter images at 20 Hz
  - ADIS16448 IMU at 200 Hz
  - Kalibr calibration file can be found [here](https://drive.google.com/file/d/1I0C-z3ZrTKne4bdbgBI6CtH1Rk4EQim0/view?usp=sharing)
* Ironsides Datasets:
  - Core visual-inertial sensor is the [ironsides](https://arxiv.org/pdf/1710.00893v1.pdf)
  - Has two [Reach RTK](https://docs.emlid.com/reach/) one subscribed to a base station for corrections
  - Stereo global shutter fisheye images at 20 Hz
  - InvenSense IMU at 200 Hz
  - GPS fixes at 5 Hz (/reach01/tcpfix has corrections from NYSNet)
  - Kalibr calibration file can be found [here](https://drive.google.com/file/d/1bhn0GrIYNEeAabQAbWoP8l_514cJ0KrZ/view?usp=sharing)
        
---
### [UZH-FPV Drone Racing Dataset](https://fpv.ifi.uzh.ch/)
High-speed, Aggressive 6DoF Trajectories for State Estimation and Drone Racing
![](https://fpv.ifi.uzh.ch/wp-content/uploads/2020/09/Are_We_Ready_for_Autonomous_Drone_Racing_The_UZH-FPV_Drone_Racing_Dataset.gif)
![](https://fpv.ifi.uzh.ch/wp-content/uploads/2020/11/teaser-1024x666.png)
[Dataset Files](https://fpv.ifi.uzh.ch/datasets/)

---
### [KAIST Urban Dataset](https://sites.google.com/view/complex-urban-dataset)
```
git clone https://github.com/irapkaist/irp_sen_msgs.git
git clone https://github.com/rpng/kaist2bag.git
```

---
### [KAIST VIO Dataset](https://github.com/url-kaist/kaistviodataset)
The KAIST VIO dataset is a dataset of a MAV in an indoor 3.15 x 3.60 x 2.50 meter environment which undergoes various trajectory motions. 
<table>
<tr>
<td><img src="https://user-images.githubusercontent.com/45934290/98090400-5054ec00-1ec7-11eb-9832-291dc9dbbabf.gif"></td>
<td><img src="https://user-images.githubusercontent.com/45934290/98204512-82bf2180-1f79-11eb-87c1-66ed70eaae3b.gif"></td>
</tr>
</table>
![](https://user-images.githubusercontent.com/45934290/96549200-222db480-12ea-11eb-8273-30d08be27316.png)

---
## [KITTI Vision Benchmark Suite](http://www.cvlibs.net/datasets/kitti/)
![](http://www.cvlibs.net/datasets/kitti/images/passat_sensors.jpg)
<iframe width="920" height="520" src="https://www.youtube.com/embed/KXpZ6B1YB_k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [Visual Odometry / SLAM Evaluation 2012](http://www.cvlibs.net/datasets/kitti/eval_odometry.php)
![](http://www.cvlibs.net/datasets/kitti/images/header_odometry.jpg)

### [CT-ICP: Elastic SLAM for LiDAR sensors](https://arxiv.org/abs/2109.12979)
![](https://xuwuzhou.top/images/%E8%AE%BA%E6%96%8754%E5%9B%BE%E7%89%872.png)

----
## [Homeworks]
### Ceres Solver installation
```
sudo apt-get install cmake 
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libeigen3-dev
sudo apt-get install libsuitesparse-dev
```
```
wget http://ceres-solver.org/ceres-solver-2.1.0.tar.gz
tar zxf ceres-solver-2.1.0.tar.gz
mkdir ceres-bin
cd ceres-bin
cmake ../ceres-solver-2.1.0
make -j4
make install
```

---
### VINS-Fusion
```
source_ros1
mkdir ~/catkin_vins/src
cd ~/catkin_vins/src
git clone https://github.com/rkuo/VINS-Fusion.git
cd ..
catkin build
```
*catkin build took<span style="color: red"> ~7.5 hours</span> on Celeron 1.10GHzx2 !!!*<br>
*catkin build took<span style="color: red"> ~3 hours</span> on i7-920 2.67GHzx4 !!!*<br>

* open Terminals
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
```

---
### VI-Car
Download [car.bag](https://drive.google.com/open?id=10t9H1u8pMGDOI6Q2w2uezEq5Ib-Z8tLz) 

1. run roscore
```
source_ros1
rosecore
```
2. lauch rviz
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
roslaunch vins vins_rviz.launch
```
3. run vins node
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
rosrun vins vins_node ~/catkin_vins/src/VINS-Fusion/config/vi_car/vi_car.yaml
```
4. run loop_fusion (optional)
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
rosrun loop_fusion loop_fusion_node ~/catkin_vins/src/VINS-Fusion/config/vi_car/vi_car.yaml
```
5. rosbag play YOUR_DATASET_FOLDER/car.bag
```
source_ros1
rosbag play /mnt/c/Users/user/Downloads/car.bag
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/VINS-Fusion_VI_Car_terminals.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/VINS-Fusion_VI_Car.png?raw=true)

---
### MAV (Micro Aerial Vehicle)
<ins>**Monocualr camera + IMU**</ins><br>
**MH_01_easy**: [EuRoC MAV Dataset](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets)<br>
Download [MH_01_easy](http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_01_easy/MH_01_easy.bag) 
1. run roscore
```
source_ros1
rosecore
```
2. lauch rviz
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
roslaunch vins vins_rviz.launch
```
3. run vins node
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
rosrun vins vins_node ~/catkin_vins/src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml
```
4. run loop_fusion (optional)
```
source_ros1
cd ~/catkin_vins
source devel/setup.bash
rosrun loop_fusion loop_fusion_node ~/catkin_vins/src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml
```
5. rosbag play YOUR_DATASET_FOLDER/car.bag
```
source_ros1
rosbag play /mnt/c/Users/user/Downloads/MH_01_easy.bag
```
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/VINS-Fusion_MH_01_easy_terminals.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/VINS-Fusion_MH_01_easy.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/VINS-Fusion-EoRoC-MAV-MH_01_easy.gif?raw=true)
  
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*




