---
layout: post
title: PyBullet-Gym
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

This introduction includes OpenAI Gym, Stable-Baselines3, PyBullet, and Motion-Imitation.

---
## Gym
### [OpenAI Gym](https://gym.openai.com/)
[Github](https://github.com/openai/gym)<br>

`pip install gym`<br>

```
import gym
env = gym.make("CartPole-v1")
observation = env.reset()
for _ in range(1000):
  env.render()
  action = env.action_space.sample() # your agent here (this takes random actions)
  observation, reward, done, info = env.step(action)
  if done:
    observation = env.reset()
env.close()
```

---
### [Stable Baselines 3](https://github.com/DLR-RM/stable-baselines3)
a set of reliable implementations of reinforcement learning algorithms in PyTorch.<br>
Implemented Algorithms : **A2C, DDPG, DQN, HER, PPO, SAC, TD3**.<br>
**QR-DQN, TQC, Maskable PPO** are in [SB3 Contrib](https://github.com/Stable-Baselines-Team/stable-baselines3-contrib)<br>

`pip install stable-baselines3`<br>

```
import gym

from stable_baselines3 import PPO

env = gym.make("CartPole-v1")

model = PPO("MlpPolicy", env, verbose=1)
model.learn(total_timesteps=10000)

obs = env.reset()
for i in range(1000):
    action, _states = model.predict(obs, deterministic=True)
    obs, reward, done, info = env.step(action)
    env.render()
    if done:
        obs = env.reset()

env.close()
```

---
### [RL Baselines3 Zoo](https://github.com/DLR-RM/rl-baselines3-zoo)
A Training Framework for Stable Baselines3 Reinforcement Learning Agents<br>

![](https://github.com/DLR-RM/rl-baselines3-zoo/blob/master/images/panda_pick.gif?raw=true)

**Train an agent**<br>
The hyperparameters for each environment are defined in `hyperparameters/algo_name.yml`.<br>

Train with tensorboard support:<br>
`python train.py --algo ppo --env CartPole-v1 --tensorboard-log /tmp/stable-baselines/`<br>

Save a checkpoint of the agent every 100000 steps:<br>
`python train.py --algo td3 --env HalfCheetahBulletEnv-v0 --save-freq 100000`<br>

Continue training (here, load pretrained agent for Breakout and continue training for 5000 steps):<br>
`python train.py --algo a2c --env BreakoutNoFrameskip-v4 -i rl-trained-agents/a2c/BreakoutNoFrameskip-v4_1/BreakoutNoFrameskip-v4.zip -n 5000`

---
## [Pybullet](https://pybullet.org)
Bullet Real-Time Physics Simulation<br>

![](https://pybullet.org/wordpress/wp-content/uploads/2019/03/cropped-pybullet.png)
<iframe width="474" height="356" src="https://www.youtube.com/embed/-MfUXSAehnw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

![](https://pybullet.org/wordpress/wp-content/uploads/2021/04/download.png)

<iframe width="474" height="267" src="https://www.youtube.com/embed/EFKqNKO3P60" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="474" height="267" src="https://www.youtube.com/embed/lKYh6uuCwRY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="474" height="267" src="https://www.youtube.com/embed/_QPMCDdFC3E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### [PyBullet-Gym](https://github.com/benelot/pybullet-gym)
**[rkuo2000/pybullet-gym](https://github.com/benelot/pybullet-gym)**<br>
`git clone https://github.com/rkuo2000/pybullet-gym`<br>

**Examples(with pretrained weights):** pybulletgym/examples/roboschool-weights <br>
`cp pybulletgym/examples/roboschool-weights/enjoy_TF_HumanoidPyBulletEnv_v0_2017may.py .`<br>

`python enjoy_TF_HumanoidPyBulletEnv_v0_2017may.py`<br>

**Examples:**<br>
* humanoid_a2c.py
* humanoid_ddpg.py
* humanoid_ppo.py
* humanoidrun_a2c.py
* invertedpendulum_a2c.py
* invertedpendulum_ddpg.py
* invertedpendulum_sac.py
* invertedPendulum_td3.py

---
## Motion Imitation
**Paper:** [Learning Agile Robotic Locomotion Skills by Imitating Animals](https://arxiv.org/abs/2004.00784)<br>
**Code:** [Motion Imitation in TF1.15](https://github.com/google-research/motion_imitation)<br>
**Code:** [Motion Imitation in PyTorch](https://github.com/newera-001/motor-system)<br>

![](https://xbpeng.github.io/projects/Robotic_Imitation/robotic_imitation_teaser.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/lKYh6uuCwRY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

