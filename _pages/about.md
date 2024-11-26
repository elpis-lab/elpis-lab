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

news: true # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

Wecome to the webpage of the Efficient Learning and Planning for Intelligent Systems (ELPIS) Lab! 

The Lab has a broad interest in autonomous robotic systems capable of reasoning about and interacting with the physical world. The primary goal is to develop agents that are efficient, robust, and capable of learning from real-world interactions. Current research projects focus on the integration of classical planning algorithms and state-of-the-art machine learning techniques, aiming to advance 1) [planning efficiency](\projects\efficiency), 2) [planning robustness](\projects\uncertainty), and 3) [planning from visual inputs](\projects\visual). 

If you are interested in joining the Lab please see this [page](\join\). 

<!-- ## Lab Team Photos -->

<div class="container mt-5">
  <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="/assets/img/team_pictures/team_photo_1.jpg" class="d-block w-100" alt="Team Photo 1">
      </div>
      <div class="carousel-item">
        <img src="/assets/img/team_pictures/team_photo_2.jpg" class="d-block w-100" alt="Team Photo 2">
      </div>
      <div class="carousel-item">
        <img src="/assets/img/team_pictures/team_photo_3.jpg" class="d-block w-100" alt="Team Photo 3">
      </div>
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
}
</style>

<script>
$(document).ready(function(){
    $('.carousel').carousel({
        interval: 3000
    });
});
</script>
