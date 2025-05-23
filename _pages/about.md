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

carousel:
  show_captions: true  
  images:
    - src: "/assets/img/team_pictures/team_photo_1.jpg"
      alt: "Team Photo 1"
      caption: "ELPIS Lab @ NERC 2024, UMass Amherst"
      active: true
    - src: "/assets/img/team_pictures/team_photo_4.png"
      alt: "Team Photo 3"
      caption: "Christmas Dinner Celebration 2024"
    - src: "/assets/img/team_pictures/team_photo_2.jpg"
      alt: "Team Photo 2"
      caption: ""
    - src: "/assets/img/team_pictures/Team_Dinner_5.jpg"
      alt: "Team Dinner 5"
      caption: ""
    - src: "/assets/img/team_pictures/AbhiroopHSCC.jpg"
      alt: "Abhiroop at HSCC"
      caption: "Abhiroop Presenting at HSCC 2025"

news: true # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

Wecome to the webpage of the Efficient Learning and Planning for Intelligent Systems (ELPIS) Lab! 

The Lab has a broad interest in autonomous robotic systems capable of reasoning about and interacting with the physical world. The primary goal is to develop agents that are efficient, robust, and capable of learning from real-world interactions. Current research projects focus on the integration of classical planning algorithms and state-of-the-art machine learning techniques, aiming to advance 1) [planning efficiency](/projects/efficiency), 2) [planning robustness](/projects/uncertainty), and 3) [planning from visual inputs](/projects/visual). 

If you are interested in joining the Lab please see this [page](/join). 

<!-- ## Lab Team Photos -->

<div class="container mt-5">
  <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <div class="carousel-inner">
      {% for image in page.carousel.images %}
      <div class="carousel-item {% if image.active %}active{% endif %}">
        <img src="{{ image.src }}" class="d-block w-100" alt="{{ image.alt }}">
        {% if page.carousel.show_captions and image.caption and image.caption != "" %}
        <div class="carousel-caption d-none d-md-block">
          <h5>{{ image.caption }}</h5>
        </div>
        {% endif %}
      </div>
      {% endfor %}
    </div>
    <a class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</div>

<style>
.carousel {
    max-width: 800px;
    margin: 0 auto;
}
.carousel-item img {
    max-height: 400px;
    object-fit: cover;
    filter: contrast(1.02);
    image-rendering: -webkit-optimize-contrast;
    image-rendering: crisp-edges;
    backface-visibility: hidden;
    transform: translateZ(0);
    -webkit-font-smoothing: subpixel-antialiased;
}
.carousel-caption {
    background: rgba(0, 0, 0, 0.5);
    padding: 15px;
    border-radius: 8px;
    color: rgba(255, 255, 255, 0.9) !important;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.5); 
    bottom: 20px !important;
    left: 50%;
    transform: translateX(-50%);
    width: 80%;
    max-width: 600px;
}
.carousel-caption h5 {
    color: rgba(255, 255, 255, 0.95) !important;
    font-weight: 500;
    font-size: 1.1rem;
    margin-bottom: 5px;
    letter-spacing: 0.5px;
}
.carousel-caption p {
    color: rgba(255, 255, 255, 0.85) !important;
    margin-bottom: 0;
    font-size: 0.9rem;
}
</style>

<script>
$(document).ready(function(){
    $('.carousel').carousel({
        interval: 3000
    });
});
</script>
