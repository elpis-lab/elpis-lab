---
layout: page
permalink: /mqps/
title: MQPs
description: Major Qualifying Projects advised by the ELPIS Lab, the capstone project of WPI undergraduates.
nav: true
nav_order: 6.5
---

<div class="mqp-list">
  {% assign mqp_years = site.mqps | group_by: "year" | sort: "name" | reverse %}
  {% for group in mqp_years %}
    <h2 class="mqp-year-heading">{{ group.name }}&ndash;{{ group.name | plus: 1 }}</h2>
    {% for mqp in group.items %}
      <article class="mqp-feature">
        {% if mqp.teaser %}
          <a class="mqp-feature-media" href="{{ mqp.url | relative_url }}">
            <img src="{{ mqp.teaser | relative_url }}" alt="{{ mqp.title }}" loading="lazy">
          </a>
        {% endif %}
        <div class="mqp-feature-body">
          <h3><a href="{{ mqp.url | relative_url }}">{{ mqp.title }}</a></h3>
          {% if mqp.subtitle %}<p class="mqp-feature-subtitle">{{ mqp.subtitle }}</p>{% endif %}
          {% if mqp.description %}<p class="mqp-feature-description">{{ mqp.description }}</p>{% endif %}
          <ul class="mqp-meta">
            {% if mqp.students %}
              <li><strong>Students:</strong>
                {% for person in mqp.students %}{% if person.url %}<a href="{{ person.url }}" target="_blank" rel="noopener noreferrer">{{ person.name }}</a>{% else %}{{ person.name }}{% endif %}{% unless forloop.last %}, {% endunless %}{% endfor %}
              </li>
            {% endif %}
            {% if mqp.advisors %}
              <li><strong>Advisors:</strong>
                {% for person in mqp.advisors %}{% if person.url %}<a href="{{ person.url }}" target="_blank" rel="noopener noreferrer">{{ person.name }}</a>{% else %}{{ person.name }}{% endif %}{% unless forloop.last %}, {% endunless %}{% endfor %}
              </li>
            {% endif %}
            {% if mqp.sponsor %}
              <li><strong>Sponsor:</strong>
                {% if mqp.sponsor_url %}<a href="{{ mqp.sponsor_url }}" target="_blank" rel="noopener noreferrer">{{ mqp.sponsor }}</a>{% else %}{{ mqp.sponsor }}{% endif %}
              </li>
            {% endif %}
          </ul>
          <div class="mqp-actions">
            <a class="mqp-button mqp-button--solid" href="{{ mqp.url | relative_url }}"><i class="fa-solid fa-arrow-right" aria-hidden="true"></i> Project page</a>
            {% if mqp.featured_videos %}
              <a class="mqp-button" href="{{ mqp.featured_videos[0].src | replace: 'youtube.com/embed/', 'youtube.com/watch?v=' }}" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-youtube" aria-hidden="true"></i> Video</a>
            {% endif %}
            {% if mqp.report_url %}
              <a class="mqp-button" href="{{ mqp.report_url }}" target="_blank" rel="noopener noreferrer"><i class="fa-regular fa-file-pdf" aria-hidden="true"></i> Report</a>
            {% endif %}
          </div>
        </div>
      </article>
    {% endfor %}
  {% endfor %}
</div>
