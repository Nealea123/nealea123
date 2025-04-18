---
title: "ACT Imitation Learning of Operate Box with ROS/Gazebo simulation"
date: 2024-07-06
layout: post
categories: [reproduce, imitation learning]
tags: [imitation learning, operation, manipulation]
---

## Introduction
Inspired by the utilization of dogs in sled-pulling for transportation, we introduce a cable-trailer system with a quadruped robot. The motion planning of the proposed robot system presents challenges arising from the nonholonomic constraints of the trailer, system underactuation, and hybrid interaction through the cable. To tackle these challenges, we develop a hybrid dynamics model that accounts for the cable's taut/slack status. Since it is computationally intense to directly optimize the trajectory, we first propose a search algorithm to compute a sub-optimal trajectory as the initial solution. Then, a novel collision avoidance constraint based on the geometric shapes of objects is proposed to formulate the trajectory optimization problem for the hybrid system. The proposed trajectory planning method is implemented on a Unitree A1 quadruped robot with a customized cable-trailer and validated through experiments.

> A preprint of the paper is available at <kbd><a href="https://arxiv.org/abs/2404.12220" target="_blank" style="text-decoration: none; color: inherit;" >arXiv</a></kbd>
{: .prompt-tip }

<!-- , which is submitted to IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2024 -->

## Motivation
![Motivation](/images/slednav/sledinspir.bmp)

## Method
![Method](/images/slednav/sledmethod.bmp)
![Framework](/images/slednav/sledframe.bmp)

## Experiment
We validate our planning method through numerical simulation and conduct real-world experiments in various scenarios to demonstrate its effectiveness. The trajectory optimization problem is formulated using [CasADi](https://web.casadi.org/), with [IPOPT](https://github.com/coin-or/Ipopt) serving as the solver.

![Experiment](/images/slednav/sledtest.bmp)

**Experiment result**: tractor average speed **<font color="red">≈1m/s</font>**, trailer position error **<font color="red"><10cm</font>**, and trailer yaw angle error **<font color="red"><5.25°</font>** (calculated by motion capture system)