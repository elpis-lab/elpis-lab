---
layout: mqp
title: GRACE
subtitle: General Robot Assistant for Common Errands
description: A mobile manipulator that navigates unknown environments, finds a target object, picks it up, and places it at a semantic goal location.
year: 2024
completed: May 2025
report_url: https://digital.wpi.edu/concern/student_works/nz806415w?locale=en
permalink: /mqps/grace/
teaser: /assets/img/mqps/grace.jpg
teaser_caption: GRACE searching for a target object on a table
students:
  - name: Brent Weiffenbach
    url: https://www.linkedin.com/in/brent-weiffenbach/
  - name: Alexander Beck
    url: https://www.linkedin.com/in/alexanderbeck0/
  - name: Gwenaelle DeLeo
    url: https://www.linkedin.com/in/gwen-deleo-abb6492a7/
advisors:
  - name: Prof. Jing Xiao
    url: https://www.wpi.edu/people/faculty/jxiao2
  - name: Prof. Constantinos Chamzas
    url: https://cchamzas.com/
  - name: Prof. Reza Ebadi
    url: https://www.wpi.edu/people/faculty/rebadi
featured_videos:
  - title: GRACE demo
    caption: GRACE searching for an object, picking it up, and placing it at a goal location.
    src: https://www.youtube.com/embed/ce3OphPrwlA
---

## Overview

Mobile manipulation enables robots to perform complex tasks using a mobile base and one or more manipulators. GRACE is a mobile manipulator that adds a 3D-printed 6-DoF arm to the open-source TurtleBot2 platform to perform household errands.

The team equipped GRACE with software for:

- Simultaneous localization and mapping (SLAM)
- Perception of semantic objects using YOLO object detection
- Pick-and-place motion planning
- Arduino controllers for the manipulator

GRACE navigates unknown environments, searches for a target object, picks it up, and navigates to a semantic goal location to place it.
