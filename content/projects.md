---
title: "Projects"
layout: "single"
---

## Deep Reinforcement Learning Nanodegree Projects

*Udacity / NVIDIA Institute, March 2026*

Three deep RL projects covering navigation, continuous control, and multi-agent collaboration, completed as part of the Deep Reinforcement Learning Nanodegree (Udacity / NVIDIA Institute). **Navigation:** trained a DQN agent to collect yellow bananas while avoiding blue ones in a large 3D environment. **Continuous Control:** trained a double-jointed arm (Reacher) to follow a target location using PPO. **Collaboration:** trained two agents to play tennis cooperatively using Multi-Agent PPO, maximizing the number of consecutive volleys.

<div class="img-gallery">
  <div class="img-row">
    <img src="/pics/banana.gif" alt="Navigation — Banana collector" style="height: 150px; width: auto; border-radius: 6px;" />
    <img src="/pics/reacher.gif" alt="Continuous Control — Reacher" style="height: 150px; width: auto; border-radius: 6px;" />
  </div>
  <img src="/pics/tennis.gif" alt="Collaboration — Tennis" style="height: 150px; width: auto; border-radius: 6px;" />
</div>

**Keywords:** Deep Reinforcement Learning, DQN, PPO, Multi-Agent PPO, Unity ML-Agents, Python

---

## Humanoid Control with Parallel Mechanisms

*LAAS-CNRS Gepetto, 2024–2025*

Developed a complete framework for controlling humanoid robots equipped with closed-kinematic actuators (parallel knee and ankle mechanisms). The approach introduces a compact differential analytical model of the transmission that enables efficient trajectory optimization via Crocoddyl/FDDP and the transfer of impedance gains from serial space to actuator space for RL deployment. Validated in simulation (MuJoCo, Isaac Lab) and on the real Bipetto robot.

<div class="img-row">
  <img src="/pics/bipettosim.gif" alt="Bipetto simulation" style="height: 220px; width: auto; border-radius: 6px;" />
  <img src="/pics/bipetto.gif" alt="Bipetto real robot" style="height: 220px; width: auto; border-radius: 6px;" />
</div>

**Keywords:** Optimal Control, Reinforcement Learning, Parallel Mechanisms, Pinocchio, Crocoddyl, Isaac Lab, MuJoCo, Python

[Paper (arXiv:2503.22459)](https://arxiv.org/abs/2503.22459)

---

## Parkour Trajectory Optimization on Solo12

*LAAS-CNRS Gepetto, 2024*

Trajectory optimization for dynamic parkour motions on the Solo12 quadruped robot, pushing the robot to its joint limits through challenging multi-contact tasks. Uses constrained optimal control solver (CSQP) with collision avoidance integrated into the optimal control problem.

<div class="img-gallery">
  <div class="img-row">
    <img src="/pics/solotraj.gif" alt="Solo12 trajectory" style="height: 200px; width: auto; border-radius: 6px;" />
    <img src="/pics/solosim.gif" alt="Solo12 simulation" style="height: 200px; width: auto; border-radius: 6px;" />
  </div>
  <img src="/pics/solo.gif" alt="Solo12 real robot" style="height: 200px; width: auto; border-radius: 6px;" />
</div>

**Keywords:** Trajectory Optimization, Optimal Control, Quadruped Robotics, Python, Pinocchio, Crocoddyl

---

## Robot Simulation Integration at PAL Robotics

*PAL Robotics, Barcelona, 2023*

Integration of humanoid and mobile manipulator robot simulations in MuJoCo. Bimanual workspace analysis using ROS and C++. Deployment tooling with Docker and Bash scripts for NVIDIA Jetson embedded boards.

<div class="img-row">
  <img src="/pics/tiago.png" alt="Tiago robot" style="height: 200px; width: auto; border-radius: 6px;" />
  <img src="/pics/tiagopro.png" alt="Tiago Pro robot" style="height: 200px; width: auto; border-radius: 6px;" />
  <img src="/pics/talos.png" alt="Talos robot" style="height: 200px; width: auto; border-radius: 6px;" />
</div>

**Keywords:** MuJoCo, ROS, C++, Python, Docker, NVIDIA Jetson
