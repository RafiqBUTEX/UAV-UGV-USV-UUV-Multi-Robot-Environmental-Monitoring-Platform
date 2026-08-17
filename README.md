# UAV-UGV-USV-UUV Multi-Robot Environmental Monitoring Platform

A simulation-first robotics platform integrating **UAV, UGV, USV, and UUV** systems for autonomous environmental and ecological monitoring, built with **ROS 2 Humble, Gazebo Harmonic, and ArduPilot SITL**.

The project focuses on developing a unified multi-robot architecture in which aerial, ground, surface, and underwater vehicles can eventually cooperate for environmental sensing, surveying, navigation, perception, and ecological monitoring.

## Overview

This project started as a hybrid **surface/underwater autonomous vehicle (USV/UUV)** simulation and is evolving toward a broader multi-robot environmental monitoring platform.

## System Architecture
![System architecture](architecture.png)

The long-term system combines:

- 🛩️ **UAV** — aerial surveying and communication relay
- 🚙 **UGV** — shore-based operations and logistics
- 🚤 **USV** — surface navigation, environmental sensing, and communication bridge
- 🌊 **UUV** — underwater navigation, sensing, mapping, and ecological monitoring

Development is **simulation-first**, with a future path toward real robotic hardware.

---

## Technology Stack

### Robotics & Middleware

- **ROS 2 Humble**
- **ArduPilot SITL**
- **MAVLink**
- **MAVROS**
- **C++ / Python**

### Simulation

- **Gazebo Harmonic**
- **gz-sim 8**
- ArduPilot's official Gazebo integration
- SDF-based vehicle and world modeling

### Navigation & Localization

- **Nav2**
- `robot_localization`
- EKF-based sensor fusion
- GPS waypoint navigation
- Planned GPS-denied underwater navigation

### Perception & Mapping

- **YOLOv8**
- **OpenCV**
- RTAB-Map
- ORB-SLAM3
- Planned underwater vision/sonar perception

### AI & Control

- Reinforcement learning for future station-keeping and depth-control research
- PID baseline comparison
- Data-driven environmental monitoring

---

## Current Project Status

### ROS 2 Workspace

The current `suv_ws` workspace contains four ROS 2 packages:

```text
suv_ws/
└── src/
    ├── suv_bringup/
    ├── suv_description/
    ├── suv_navigation/
    └── suv_perception/
