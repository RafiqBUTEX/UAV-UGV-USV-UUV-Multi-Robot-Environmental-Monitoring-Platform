# UAV-UGV-USV-UUV Multi-Robot Environmental Monitoring Platform

A simulation-first multi-robot robotics platform integrating **UAV, UGV, USV, and UUV** systems for autonomous environmental and underwater ecology monitoring.

## Overview

The project explores coordinated autonomous operation of aerial, ground, surface, and underwater vehicles using **ROS 2, Gazebo Harmonic, and ArduPilot SITL**.

- 🛩️ **UAV** — aerial survey and communication relay
- 🚙 **UGV** — shore-based operations and support
- 🚤 **USV** — surface navigation and environmental monitoring
- 🌊 **UUV** — underwater sensing, mapping, and ecological monitoring

![Architecture](architecture.png)

The system is being developed in simulation first, with a future path toward real-world robotic platforms.

## Tech Stack

- **Simulation:** Gazebo Harmonic (gz-sim 8), ArduPilot Gazebo plugin, SDF
- **Autopilot:** ArduPilot SITL (Copter / Rover / Rover-Skid / ArduSub)
- **Middleware:** ROS 2 Humble, MAVROS, MAVLink
- **Navigation:** Nav2, `robot_localization`
- **Perception:** YOLOv8, OpenCV
- **Mapping & SLAM:** RTAB-Map / ORB-SLAM3
- **Reference USV:** ArduPilot BlueBoat

## Current Status

- ROS 2 workspace (`suv_ws`) with four packages: bringup, description, navigation, and perception
- ArduPilot Rover SITL built from source and verified
- Gazebo Harmonic simulation environment established
- Migrated the development pipeline from Gazebo Classic to Gazebo Harmonic
- Resolved VirtualBox-specific rendering issues
- Validated the ArduPilot SITL ↔ Gazebo Harmonic pipeline using an ArduPilot reference vehicle
- Developed a custom water world
- Developed and tested an initial custom boat hull
- Debugged SDF, joint-scoping, plugin, and physics-related issues
- Integrated ArduPilot's BlueBoat reference model for continued USV development
- Currently working on reliable USV buoyancy and propulsion in Gazebo Harmonic

## Roadmap

### Phase 1 — Surface Autonomy
Water world + BlueBoat USV, buoyancy/thrust, GPS waypoint navigation, obstacle and buoy detection.

### Phase 2 — Dive & Resurface
Depth and pitch control with autonomous dive → hold → resurface behavior.

### Phase 3 — Underwater Localization
GPS-denied navigation using simulated DVL + IMU with EKF sensor fusion.

### Phase 4 — Underwater Perception & Mapping
Simulated sonar and/or vision, SLAM, and underwater object detection.

### Phase 5 — Autonomous Mission
Surface transit → dive → underwater task → resurface → return.

### Phase 6 — Reinforcement Learning
RL-based depth-hold and station-keeping under simulated current and wave disturbances.

### Phase 7 — Multi-Robot Expansion
Coordinated **UAV + UGV + USV + UUV** operation with multi-vehicle SITL, ROS 2 namespaces, mission coordination, and task allocation.

## Development Environment

- Ubuntu 22.04 LTS
- ROS 2 Humble
- Gazebo Harmonic
- ArduPilot SITL
- Oracle VirtualBox

## Getting Started

```bash
# Source ROS 2
source /opt/ros/humble/setup.bash

# Source the workspace
source ~/suv_ws/install/setup.bash

# Launch the water world
gz sim -v4 -r ~/suv_ws/src/suv_bringup/worlds/water_world.world

# In a separate terminal, start ArduPilot Rover SITL
cd ~/ardupilot/Rover
sim_vehicle.py -v Rover -f rover-skid --model JSON --console --map
