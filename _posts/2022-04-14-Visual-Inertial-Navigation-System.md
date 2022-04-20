---
layout: post
title: 視覺慣性導航系統
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to VIO, OpenVINS, VINS-Fusion and Datasets (EuRoC-MAV, TUM Visual-Inertial Dataset, UZH-FPV Drone Racing Dataset, KAIST Urban Dataset, KAIST VIO Dataset).

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
### [Visual-Inertial Odometry Benchmarking](https://www.ifi.uzh.ch/ifi/rpg/docs/ICRA18_Delmerico.pdf)
<iframe width="826" height="465" src="https://www.youtube.com/embed/ymI3FmwU9AY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
### SVO: Fast Semi-Direct Monocular Visual Odometry
<iframe width="826" height="465" src="https://www.youtube.com/embed/hR8uq1RTUfA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="826" height="465" src="https://www.youtube.com/embed/2YnIMfw6bJY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="826" height="465" src="https://www.youtube.com/embed/gr00Bf0AP1k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
References:<br>
* [SVO: Semi-Direct Visual Odometry for Monocular and Multi-Camera Systems](https://www.ifi.uzh.ch/dam/jcr:f2deef0e-788e-4d4e-b97b-c1d463dc3316/TRO17_Forster-SVO.pdf)
* [SVO: Fast Semi-Direct Monocular Visual Odometry](https://www.ifi.uzh.ch/dam/jcr:e9b12a61-5dc8-48d2-a5f6-bd8ab49d1986/ICRA14_Forster.pdf)
  - [Code](https://github.com/uzh-rpg/rpg_svo)
* [REMODE: Probabilistic, Monocular Dense Reconstruction in Real Time](https://www.ifi.uzh.ch/dam/jcr:7edf1f0c-aaa1-470f-930a-f77faec4a2f0/ICRA14_Pizzoli.pdf)
  - [Code](https://github.com/uzh-rpg/rpg_open_remode)
<iframe width="826" height="465" src="https://www.youtube.com/embed/QTKd5UWCG0Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
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
### 
[The Integration of GPS-BDS Real-Time Kinematic Positioning and Visual–Inertial Odometry Based on Smartphones](file:///home/rkuo/Downloads/ijgi-10-00699-v2.pdf)

---
## Visual-Inertial Navigation System (VINS)

### [Robot Perception and Navigation Group(RPNG)](https://sites.udel.edu/robot/)
* [Research](https://sites.udel.edu/robot/research/)
* [Publications](https://sites.udel.edu/robot/publications/)
  - [MIMC-VINS: A Versatile and Resilient Multi-IMU Multi-Camera Visual-Inertial Navigation System](https://arxiv.org/abs/2006.15699)
  <iframe width="789" height="444" src="https://www.youtube.com/embed/my1IjdJ4irY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  - Multi-IMU VIO: [Sensor-Failure-Resilient Multi-IMU Visual-Inertial Navigation](https://udel.edu/~pgeneva/downloads/papers/c06.pdf)
  <iframe width="789" height="444" src="https://www.youtube.com/embed/TqbzqLgnIZc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [OpenINVS](https://github.com/rpng/open_vins)
**paper:** [OpenVINS: A Research Platform for Visual-Inertial Estimation](http://udel.edu/~pgeneva/downloads/papers/c10.pdf)<br>

The OpenVINS project houses some core computer vision code along with a state-of-the art filter-based visual-inertial estimator. The core filter is an [Extended Kalman filter](https://en.wikipedia.org/wiki/Extended_Kalman_filter) which fuses inertial information with sparse visual feature tracks. These visual feature tracks are fused leveraging the [Multi-State Constraint Kalman Filter (MSCKF)](https://www-users.cse.umn.edu/~stergios/papers/ICRA07-MSCKF.pdf) sliding window formulation which allows for 3D features to update the state estimate without directly estimating the feature states in the filter. 

### [Documentation](https://docs.openvins.com/)<br>
**Codebase Extensions:**<br>
* [vicon2gt](https://github.com/rpng/vicon2gt) - This utility was created to generate groundtruth trajectories using a motion capture system (e.g. Vicon or OptiTrack) for use in evaluating visual-inertial estimation systems. Specifically we calculate the inertial IMU state (full 15 dof) at camera frequency rate and generate a groundtruth trajectory similar to those provided by the EurocMav datasets. Performs fusion of inertial and motion capture information and estimates all unknown spacial-temporal calibrations between the two sensors.

* [ov_maplab](https://github.com/rpng/ov_maplab) - This codebase contains the interface wrapper for exporting visual-inertial runs from OpenVINS into the ViMap structure taken by maplab. The state estimates and raw images are appended to the ViMap as OpenVINS runs through a dataset. After completion of the dataset, features are re-extract and triangulate with maplab's feature system. This can be used to merge multi-session maps, or to perform a batch optimization after first running the data through OpenVINS. Some example have been provided along with a helper script to export trajectories into the standard groundtruth format.

* [ov_secondary](https://github.com/rpng/ov_secondary) - This is an example secondary thread which provides loop closure in a loosely coupled manner for OpenVINS. This is a modification of the code originally developed by the HKUST aerial robotics group and can be found in their [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion) repository. Here we stress that this is a loosely coupled method, thus no information is returned to the estimator to improve the underlying OpenVINS odometry. This codebase has been modified in a few key areas including: exposing more loop closure parameters, subscribing to camera intrinsics, simplifying configuration such that only topics need to be supplied, and some tweaks to the loop closure detection to improve frequency.

### [Getting started guide](https://docs.openvins.com/getting-started.html)
[Installation Guide](https://docs.openvins.com/gs-installing.html)<br>
* [Ubuntu 20.04 ROS 1 Noetic (uses OpenCV 4.2)](http://wiki.ros.org/noetic/Installation/Ubuntu)<br>
* [Ubuntu 20.04 ROS 2 Galactic (uses OpenCV 4.2)](https://docs.ros.org/en/galactic/)<br>

* **ROS1 Install**
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt-get update
export ROS1_DISTRO=noetic # kinetic=16.04, melodic=18.04, noetic=20.04
sudo apt-get install ros-$ROS1_DISTRO-desktop-full
sudo apt-get install python3-catkin-tools python3-osrf-pycommon # ubuntu 20.04
sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev
```
```
echo "alias source_ros1=\"source /opt/ros/$ROS1_DISTRO/setup.bash\"" >> ~/.bashrc
echo "alias source_devel=\"source devel/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```

* **ROS2 Install**
```
sudo apt update && sudo apt install curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt-get update
export ROS2_DISTRO=galactic # dashing=18.04, galactic=20.04
sudo apt install ros-$ROS2_DISTRO-desktop
sudo apt-get install ros-$ROS2_DISTRO-ros2bag ros-$ROS2_DISTRO-rosbag2* # rosbag utilities (seems to be separate)
sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev
pip install -U colcon-common-extensions
```
```
echo "alias source_ros2=\"source /opt/ros/$ROS2_DISTRO/setup.bash\"" >> ~/.bashrc
echo "alias source_install=\"source install/setup.bash\"" >> ~/.bashrc
source ~/.bashrc
```

* **Cloning the OpenVINS Project**
```
mkdir -p ~/workspace/catkin_ws_ov/src/
cd ~/workspace/catkin_ws_ov/src/
git clone https://github.com/rpng/open_vins/
cd ..
catkin build # ROS1
colcon build # ROS2
colcon build --event-handlers console_cohesion+ --packages-select ov_core ov_init ov_msckf ov_eval # ROS2 with verbose output
```

* **[Ceres Solver installation](http://ceres-solver.org/installation.html)**
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
### [VINS-Mobile](https://github.com/HKUST-Aerial-Robotics/VINS-Mobile)
<iframe width="826" height="465" src="https://www.youtube.com/embed/0mTXnIfFisI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* [The Integration of GPS/BDS Real-Time Kinematic Positioning and Visual–Inertial Odometry Based on Smartphones](https://mdpi-res.com/d_attachment/ijgi/ijgi-10-00699/article_deploy/ijgi-10-00699-v2.pdf)

---
### [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono)
The framework of VINS-Mono
![](https://www.mdpi.com/ijgi/ijgi-10-00699/article_deploy/html/images/ijgi-10-00699-g003.png)

---
## [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)
[VINS Fusion 笔记](https://scm_mos.gitlab.io/slam/VINS-FUSION/)<br>
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/blob/master/support_files/image/vins_logo.png?raw=true)

```
cd ~/catkin_ws/src
git clone https://github.com/HKUST-Aerial-Robotics/VINS-Fusion.git
cd ../
catkin build
source ~/catkin_ws/devel/setup.bash
```

---
### EuRoC
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/raw/master/support_files/image/euroc.gif)
* Monocualr camera + IMU
  - `roslaunch vins vins_rviz.launch`
  - `rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml`
  - (optional) `rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml`
  - `rosbag play YOUR_DATASET_FOLDER/MH_01_easy.bag`

* Stereo cameras + IMU
  - `roslaunch vins vins_rviz.launch`
  - `rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_stereo_imu_config.yaml`
  - (optional) `rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_stereo_imu_config.yaml`
  - `rosbag play YOUR_DATASET_FOLDER/MH_01_easy.bag`
  
* Stereo cameras
  - `roslaunch vins vins_rviz.launch`
  - `rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_stereo_config.yaml`
  - (optional) `rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/euroc/euroc_stereo_config.yaml`
  - `rosbag play YOUR_DATASET_FOLDER/MH_01_easy.bag`

---
### KITTI Example
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
### VINS-Fusion on car demonstration
![](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/raw/master/support_files/image/car_gif.gif)
* VI-Car
  - Download [car bag](https://drive.google.com/open?id=10t9H1u8pMGDOI6Q2w2uezEq5Ib-Z8tLz) to YOUR_DATASET_FOLDER.
  - `roslaunch vins vins_rviz.launch`
  - `rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion/config/vi_car/vi_car.yaml`
  - (optional) `rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/vi_car/vi_car.yaml`
  - `rosbag play YOUR_DATASET_FOLDER/car.bag`

---
### VIO 
VIO is not only a software algorithm, it heavily relies on hardware quality. 
For beginners, we recommend you to run VIO with professional equipment, which contains global shutter cameras and hardware synchronization.
* Configuration file
Write a config file for your device. You can take config files of EuRoC and KITTI as the example.

* Camera Calibration
```
cd ~/catkin_ws/src/VINS-Fusion/camera_models/camera_calib_example/
rosrun camera_models Calibrations -w 12 -h 8 -s 80 -i calibrationdata --camera-model pinhole
```

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
## [Visual Odometry / SLAM Evaluation 2012](http://www.cvlibs.net/datasets/kitti/eval_odometry.php)

### [CT-ICP: Elastic SLAM for LiDAR sensors](https://arxiv.org/abs/2109.12979)
It is integrated with the python project [pyLiDAR-SLAM](https://github.com/Kitware/pyLiDAR-SLAM) which gives access to more datasets.
![](https://github.com/jedeschaud/ct_icp/raw/master/doc/aggregated.GIF)
![](https://github.com/jedeschaud/ct_icp/raw/master/doc/keypoints_gif.GIF)
  
<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


