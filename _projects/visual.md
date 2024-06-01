---
layout: page
title: Visual Task Planning
description: Learning to Plan Directly from Images 
img: assets/img/research/vision_based_planning.jpg
importance: 3
category: Research Areas
---

The emerging research area of visual task planning attempts to learn representations suitable for planning directly from visual inputs, alleviating the need for accurate geometric models. Current methods commonly assume that similar visual observations correspond to similar states in the task planning space. However, observations from sensors are often noisy
with several factors that do not alter the underlying state, for example, different lightning conditions, different viewpoints, or irrelevant background objects. These variations result in visually dissimilar images that correspond to the same task state. Achieving robust abstract state representations for real world tasks is an important research area that requires further investigation.


<div class="publications">
<left> <h2><span style="color: var(--global-theme-color)"> Relevant Publications </span></h2> </left>
{% bibliography -f papers -q @*[keyword1=visual] || @*[keyword2=visual] || @*[keyword3=visual]%}
</div>