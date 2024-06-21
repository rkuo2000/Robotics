---
layout: post
title: Reinforcement Learning for Autonomous Driving 
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to Autonomous Driving with Reinforcement Learning

---
## Indoor Autonomous Driving

### [Autonomous Indoor Robot Navigation](https://arxiv.org/abs/2005.13857)
![](https://d3i71xaburhd42.cloudfront.net/8a47843c2e664e5e7e218e2d891726d023619403/3-Figure4-1.png)

---
### DDPG 路徑規劃
**Blog:** [智慧送餐服務型機器人導航路徑之設計](https://www.phdbooks.com.tw/cn/magazine/detail/1225)<br>
路徑跟隨器有四個主軸：<br>
* 送餐路徑生成：從文件或上層發佈訊息獲取預先定義的路徑。
* 編輯航線路徑點：清除路徑中不合適的航線路徑點。
* MFAC無模型自適應控制之航段管制：自動調整送餐路徑之導航點之間的航段長度，依序共分成路徑跟隨之依據以及MFAC無模型自適應控制之應用。
* DWA之區域路徑傳遞：依照MFAC調整之結果，產出相關生成路徑，並以DWA進行區域設定。

* **自走車基於DDPG的室內路徑規劃**<br>
<iframe width="506" height="285" src="https://www.youtube.com/embed/TNRjb8q6XxM" title="自走車基於DDPG的室內路徑規劃" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## RoboCar Gym

### Pybullet-RoboCar
**Blog:** <br>
[Creating OpenAI Gym Environments with PyBullet (Part 1)](https://gerardmaggiolino.medium.com/creating-openai-gym-environments-with-pybullet-part-1-13895a622b24)<br>
[Creating OpenAI Gym Environments with PyBullet (Part 2)](https://gerardmaggiolino.medium.com/creating-openai-gym-environments-with-pybullet-part-2-a1441b9a4d8e)<br>
![](https://media0.giphy.com/media/VI3OuvQShK3gzENiVz/giphy.gif?cid=790b761131bda06b74fcd9bb06c6a43939cf446edf403a68&rid=giphy.gif&ct=g)

---
### [Carla-Gym](https://github.com/PacktPublishing/Hands-On-Intelligent-Agents-with-OpenAI-Gym/tree/master/ch7#2-carla-gym)
![](https://user-images.githubusercontent.com/4770482/149642030-9a5fc2b0-9268-45cc-9328-04f2b2e423e6.gif)

---
### [OpenAI Gym Environments for Donkey Car](https://github.com/tawnkramer/gym-donkeycar)
* [Documentation](https://gym-donkeycar.readthedocs.io/en/latest/)
* Download [simulator binaries](https://github.com/tawnkramer/gym-donkeycar/releases)
* [Donkey Simulator User Guide](https://docs.donkeycar.com/guide/simulator/)
![](https://docs.donkeycar.com/assets/sim_screen_shot.png)

---
## End-to-End RL

### [End-to-end Reinforcement Learning of Robotic Manipulation with Robust Keypoints Representation](https://arxiv.org/pdf/2202.06027.pdf)
![](https://github.com/rkuo2000/EdgeAI-course/blob/main/images/End-to-End_Reinforcement_Learning.png?raw=true)


<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


