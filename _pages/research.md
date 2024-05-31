---
layout: page
title: Research 
permalink: /research/
description: 
nav: false 
nav_order: 3
display_categories: [work, fun]
horizontal: false
---
Robots and other AI-enabled systems offer tremendous promise for supporting humans in a variety of physical and cognitive tasks. For instance, imagine an AI Coach that can train humans and mitigate preventable errors. Or, a Robotic Assistant that can perform chores (both at work and home) given high-level task specifications.

To deliver on this promise, AI-enabled systems will need new technology to reason about humans and exhibit beneficial interaction. This new technology will also be critical to avoid unintended side effects of AI, such as disuse, misuse, and bias. Our research aims to generate this new technology, in the form of algorithmic advances and interactive systems.

For more details, please check out our contributions by research areas and research projects.
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
