---
layout: about
title: About 
permalink: /

profile:
  align: right 
  image: logo1.jpg
  image_circular: true # crops the image to make it circular
  more_info: >
    <p>UH200B, Unity Hall</p>
    <p>100 Institute Rd</p>
    <p>Worcester, MA 01609</p>

research_focuses:
  autoplay_ms: 6500
  items:
    - title: Planning Robustness
      description: We build robust planners that reason under uncertainty and partial observability to improve safety and reliability.
      link: /projects/uncertainty
      link_text: Explore Robustness Research
      video: /assets/video/planning_robust.mp4
    - title: Planning Efficiency
      description: We design planning systems that reduce computation time while retaining high-quality trajectories in high-dimensional spaces.
      link: /projects/efficiency
      link_text: Explore Efficiency Research
      video: /assets/video/planning_fast.mp4
    - title: Planning from Visual Inputs
      description: We investigate representations that enable task and motion planning directly from image observations in real-world scenes.
      link: /projects/visual
      link_text: Explore Vision Research
      video: /assets/video/visual_planning.mp4

news: true # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

Welcome to the webpage of the Efficient Learning and Planning for Intelligent Systems (ELPIS) Lab.

The Lab has a broad interest in autonomous robotic systems capable of reasoning about and interacting with the physical world. The primary goal is to develop agents that are efficient, robust, and capable of learning from real-world interactions. Current research projects focus on the integration of classical planning algorithms and state-of-the-art machine learning techniques, aiming to advance 1) [planning efficiency](/projects/efficiency), 2) [planning robustness](/projects/uncertainty), and 3) [planning from visual inputs](/projects/visual).

If you are interested in joining the Lab please see this [page](/join).

<section class="landing-focus-section">
  <div class="landing-focus-header">
    <h2>Research Focus Areas</h2>
    <p>Our core work spans three complementary themes that shape the lab's research agenda.</p>
  </div>

  <div
    id="researchFocusCarousel"
    class="carousel slide carousel-fade elpis-carousel research-focus-carousel"
    data-ride="carousel"
    data-interval="{{ page.research_focuses.autoplay_ms | default: 6500 }}"
    data-pause="hover"
  >
    <ol class="carousel-indicators">
      {% for focus in page.research_focuses.items %}
        <li
          data-target="#researchFocusCarousel"
          data-slide-to="{{ forloop.index0 }}"
          class="{% if focus.active or forloop.first %}active{% endif %}"
        ></li>
      {% endfor %}
    </ol>
    <div class="carousel-inner">
      {% for focus in page.research_focuses.items %}
        <div class="carousel-item {% if focus.active or forloop.first %}active{% endif %}">
          <div class="research-focus-slide row no-gutters align-items-center">
            <div class="col-lg-5">
              <div class="research-focus-copy">
                <p class="focus-kicker">Research Focus {{ forloop.index }}</p>
                <h3>{{ focus.title }}</h3>
                <p>{{ focus.description }}</p>
                <a class="btn btn-sm btn-outline-primary mt-2" href="{{ focus.link | relative_url }}">
                  {{ focus.link_text }}
                </a>
              </div>
            </div>
            <div class="col-lg-7">
              <div class="research-focus-media">
                {% if focus.video %}
                  <video autoplay muted loop playsinline preload="metadata" poster="{{ focus.poster | relative_url }}">
                    <source src="{{ focus.video | relative_url }}" type="video/mp4">
                  </video>
                {% else %}
                  <img src="{{ focus.poster | relative_url }}" alt="{{ focus.title }}">
                {% endif %}
                <span class="research-focus-media-label">{{ focus.title }}</span>
              </div>
            </div>
          </div>
        </div>
      {% endfor %}
    </div>

    <a class="carousel-control-prev" href="#researchFocusCarousel" role="button" data-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>

    <a class="carousel-control-next" href="#researchFocusCarousel" role="button" data-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</section>

<script>
$(function () {
    $("#researchFocusCarousel").carousel({
        interval: {{ page.research_focuses.autoplay_ms | default: 6500 }},
        pause: "hover"
    });
});
</script>
