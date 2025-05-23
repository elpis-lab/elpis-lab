---
layout: page
permalink: /publications/
title: Publications
description: "* denotes equal contribution." 
years: [2025, 2024, 2023, 2022, 2021, 2020, 2019]
nav: true
nav_order: 4 
---

<style>
.publications h1 {
  text-align: left !important;
}
</style>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2025 </span></h1>
{% bibliography -f papers -q @*[year=2025] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2024 </span></h1>
{% bibliography -f papers -q @*[year=2024] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2023 </span></h1>
{% bibliography -f papers -q @*[year=2023] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2022 </span></h1>
{% bibliography -f papers -q @*[year=2022] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2021 </span></h1>
{% bibliography -f papers -q @*[year=2021] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2020 </span></h1>
{% bibliography -f papers -q @*[year=2020] %}
</div>

<div class="publications">
<h1><span style="color: var(--global-theme-color)"> 2019 </span></h1>
{% bibliography -f papers -q @*[year=2019] %}
</div>