---
layout: mqp
title: Toward Automated Parachute Packing
subtitle: Pack to The Future - Multi-Arm Robotic Vision-Guided Line Stowing
description: A robotic system for automating parachute line stowing through teleoperation and autonomous control
year: 2025
permalink: /mqps/pack-to-the-future/
teaser: /assets/img/mqps/pack-to-the-future.jpg
teaser_caption: The robotic arm stowing parachute suspension lines
authors:
  - name: MQP Team
affiliation: Worcester Polytechnic Institute · ELPIS Lab
sponsor: U.S. Army Natick Soldier Systems Center (NSSC)
featured_videos:
  - title: Best Stow Demonstration
    caption: Vision-guided robotic line stowing in action
    src: https://www.youtube.com/embed/iWUgX9Byj0E
    external: true
---

## Project Overview

The U.S. Army is facing a future shortfall of Military Occupational Specialty (MOS) 92R parachute riggers, which impacts the ability to maintain readiness and sustain logistics operations. Personnel parachute inspection and packing is a methodical, life-saving process with multiple pre-defined checkpoints for quality assurance.

This MQP focused on automating a critical step in parachute packing: **line stowing**—organizing, folding, and securing suspension lines to prevent tangling and ensure smooth deployment.

## Project Scope

Rather than attempting full automation (which is impractical in the short term), the team designed a system where a robotic manipulator **threads parachute lines through a set of hoops** in a structured manner, guided by computer vision.

### Project Phases

**Phase 1: Teleoperation System Development**
- Developed a teleoperated robotic system using a 6-DOF ViperX 300 robot arm
- Implemented intuitive teleoperation control for parachute line handling
- Designed specialized fixtures to assist in the line stowing process
- Evaluated system feasibility and refined mechanical/robotic components

**Phase 2: Autonomous Line Stowing**
- Enabled the robot to autonomously stow one or more lines using the designed fixtures
- Developed state estimation capabilities to track:
  - Progress (number of hoops threaded)
  - Failures (missed stows or misalignment)
  - Completion detection (task success criteria)
- Integrated RGB-D and force sensors to assist in automation
- Implemented vision-guided control for robust autonomous operation

## Sponsoring Organization

This project was generously sponsored by the [U.S. Army Natick Soldier Systems Center (NSSC)](https://www.army.mil/natick#org-about). The NSSC works to develop and test soldier equipment, ensuring readiness and sustainability of military operations.

## Key Achievements

- Successfully developed teleoperated parachute line handling system
- Implemented vision-guided autonomous line stowing
- Created specialized fixtures for robust manipulation
- Demonstrated feasibility of robotic assistance in critical military logistics
- Provided insights for human-robot collaboration in precision tasks

---

**Team Members:** A 3-5 person team of Robotics and Mechanical Engineering students from Worcester Polytechnic Institute

**Academic Year:** 2025-2026

**Hardware:** ViperX 300 6-DOF collaborative robot arm
