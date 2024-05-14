---
layout: page
permalink: /publications/
title: publications
description: "* denotes equal contribution." 
years: [2021, 2020, 2019]
nav: true
---


<div class="publications">
<center> <h1><span style="color: var(--global-theme-color)"> Journal Articles  </span></h1> </center>
{% bibliography -f papers -q @article %}
</div>


<div class="publications">
<center> <h1><span style="color: var(--global-theme-color)"> Conference Papers  </span></h1> </center>
{% bibliography -f papers -q @inproceedings %}
</div>

<div class="publications">
<center> <h1><span style="color: var(--global-theme-color)"> Workshop Papers </span></h1> </center>
{% bibliography -f papers -q @misc %}
</div>

