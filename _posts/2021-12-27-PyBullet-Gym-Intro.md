---
layout: post
title: PyBullet-Gym
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

This introduction includes PyBullet-Gym intro, Quadruped-Robot Gym, Drone Gym, and Assistive Gym.

---
## PyBullet-Gym
### [OpenAI Gym](https://gym.openai.com/)
[Github](https://github.com/openai/gym)<br>
`pip install gym`<br>

### [Stable Baselines 3](https://github.com/DLR-RM/stable-baselines3)
`pip install stable-baselines3`<br>

### [Pybullet](https://pybullet.org)
`pip install pybullet`<br>

### [PyBullet-Gym](https://github.com/benelot/pybullet-gym)
`git clone https://github.com/rkuo2000/pybullet-gym`<br>

**Examples(with pretrained weights):** pybulletgym/examples/roboschool-weights <br>
`cp pybulletgym/examples/roboschool-weights/enjoy_TF_HumanoidPyBulletEnv_v0_2017may.py .`<br>
`python enjoy_TF_HumanoidPyBulletEnv_v0_2017may.py`<br>

**humanoid examples:**<br>
* humanoid_a2c.py
* humanoid_ddpg.py
* humanoid_ppo.py
* humanoidrun_a2c.py

---
### Rex-Gym
**Code:** [Rex: an open-source quadruped robot](https://github.com/nicrusso7/rex-gym)<br>

![](https://github.com/nicrusso7/rex-gym/blob/master/images/intro.gif?raw=true)

---
### Unitree
**[Unitree Pybullet](https://github.com/unitreerobotics/unitree_pybullet)**<br>

---
## Drone Gym
### [PyBullet-Gym for Drones](https://github.com/utiasDSL/gym-pybullet-drones)
![](https://github.com/utiasDSL/gym-pybullet-drones/blob/master/files/readme_images/helix.gif?raw=true)
![](https://github.com/utiasDSL/gym-pybullet-drones/blob/master/files/readme_images/helix.png?raw=true)

---
### [Flightmare](https://github.com/uzh-rpg/flightmare)
Flightmare is a flexible modular quadrotor simulator. 
<iframe width="768" height="432" src="https://www.youtube.com/embed/m9Mx1BCNGFU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## Assistive Gym
### Assistive Gym
**Paper:** [Assistive Gym: A Physics Simulation Framework for Assistive Robotics](https://arxiv.org/abs/1910.04700)<br>
**Code:** [Healthcare-Robotics/assistive-gym](https://github.com/Healthcare-Robotics/assistive-gym)<br>
<iframe width="705" height="397" src="https://www.youtube.com/embed/EFKqNKO3P60" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Assistive VR Gym
**Paper:** [Assistive VR Gym: Interactions with Real People to Improve Virtual Assistive Robots](https://arxiv.org/abs/2007.04959)<br>
**Code:** [Healthcare-Robotics/assistive-vr-gym](https://github.com/Healthcare-Robotics/assistive-vr-gym)<br>
<iframe width="705" height="397" src="https://www.youtube.com/embed/tcyPMkAphNs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

