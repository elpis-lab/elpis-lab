---
layout: page
permalink: /publications/
title: publications
description: <span style="color:black"> * </span> denotes equal contribution. 
years: [2021, 2020, 2019]
nav: true
---


<div class="publications">
<center> <h1><span style="color:#00369f"> Journal Articles  </span></h1> </center>
{% bibliography -f papers -q @article %}
</div>


<div class="publications">
<center> <h1><span style="color:#00369f"> Conference Papers  </span></h1> </center>
{% bibliography -f papers -q @inproceedings %}
</div>

<div class="publications">
<center> <h1><span style="color:#00369f"> Workshop Papers </span></h1> </center>
{% bibliography -f papers -q @misc %}
</div>

