---
layout: page
title: Research 
permalink: /research/
description: 
nav: false 
nav_order: 3
display_categories: [Research Areas]
horizontal: false
---

I envision a world where robots can augment humans’ capabilities in extraordinary ways. Robots
could perform dangerous and routine tasks while freeing up human resources and providing a safer
working environment. Moreover, they could assist doctors and nurses in medical procedures and
help care for the elderly. The development of accurate sensors and improved actuators has laid
the groundwork for robots to achieve such advanced capabilities, sparking tremendous growth in
robotics research. As a result, robots are already operating on factory floors and vacuuming our
homes. However, we still do not have robots that function as collaborative assistants to aid us in
mundane or hazardous tasks. Outside highly structured environments, robots fail to adapt to new
situations and are unable to perform complicated tasks. For robots to work safely and reliably in
dynamic and unstructured environments, there is a pressing need for new models and algorithms
that endow robots with advanced planning capabilities.

At the core of achieving advanced robotic autonomy lies motion planning, the research field that
computes feasible paths for robots to follow. Despite the wealth of planners developed over the years,
several problems remain open. As a Ph.D. student, I have worked on three such critical problems for
planners, namely, i) planning efficiently, ii) planning under partial observability, and iii) planning
with human guidance. Towards these goals, I have primarily focused on integrating classical robot
planning methods with machine learning techniques. These classical methods are theoretically
sound algorithms with proven guarantees such as reachability and completeness. Nonetheless,
they often work only in idealized scenarios or require significant domain knowledge. Modern
machine learning methods can directly learn from real-world data showing promising results on
challenging research areas such as image recognition and language processing. However, they often
exhibit unpredictable behavior and lack theoretical guarantees. Thus, my research aims to bring
theoretically sound classical methods into practical applications through the use of machine learning
methods that leverage real world data.

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
