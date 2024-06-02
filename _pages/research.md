---
layout: page
title: Research 
permalink: /research/
description: 
nav: true 
nav_order: 3
display_categories: [Research Areas]
horizontal: false
---


Robotics holds the potential to perform dangerous and routine tasks, freeing up human resources and providing a safer working environment. Despite significant advancements, such as robots operating on factory floors and vacuuming homes, robots still struggle to function as collaborative assistants in unstructured environments, failing to adapt to new situations or perform complex tasks. To achieve safe and reliable robot operation in dynamic settings, advanced planning capabilities are crucial. 

 The ELPIS lab addresses these challenges by focusing on three critical aspects of planning: efficiency, robustness under uncertainty due to partial information, and planning in the real world through images. By integrating classical robot planning methods with modern machine learning techniques, the research aims to develop practical applications that combine theoretical soundness with the ability to learn from real-world data, ultimately enhancing robotic autonomy and functionality in diverse environments.


<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
