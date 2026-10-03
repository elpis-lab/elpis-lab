---
layout: project
title: ActivePusher
subtitle: Active Learning and Planning with Residual Physics for Nonprehensile Manipulation
description: A data-efficient framework that learns pushing dynamics from informative interactions and plans with reliable actions.
permalink: /projects/activepusher/
authors:
  - name: Zhuoyun Zhong
    url: https://www.linkedin.com/in/zhuoyunzhong/
  - name: Seyedali Golestaneh
    url: https://www.linkedin.com/in/aligolestaneh/
  - name: Constantinos Chamzas
    url: https://cchamzas.com/
venue: Accepted to ICRA 2026
affiliation: Worcester Polytechnic Institute · ELPIS Lab
awards:
  - ICRA 2026 Best Student Paper Award
  - ICRA 2026 Best Paper in Planning and Control Finalist
  - HRF 2026 Best Student Paper Award
links:
  - label: arXiv
    url: https://arxiv.org/abs/2506.04646
    icon: ai ai-arxiv
    external: true
  - label: Paper
    url: /assets/pdf/zhong2026activepusheractivelearningplanning.pdf
    icon: fa-regular fa-file-pdf
  - label: Code
    url: https://github.com/elpis-lab/ActivePusher
    icon: fa-brands fa-github
    external: true
  - label: Video
    url: https://www.youtube.com/watch?v=lxvyy61g0CY
    icon: fa-brands fa-youtube
    external: true
featured_videos:
  - title: Active learning
    caption: Collecting informative interactions improves pushing dynamics model efficiently.
    src: /assets/projects/activepusher/videos/active-learning.mp4
    poster: /assets/projects/activepusher/videos/active-learning.webp
  - title: Active planning
    caption: Uncertainty-aware planning favors reliable actions during task execution.
    src: /assets/projects/activepusher/videos/active-planning.mp4
    poster: /assets/projects/activepusher/videos/active-planning.webp
---

<section aria-labelledby="overview-heading">
  <h2 id="overview-heading">Learn where uncertain. Plan where reliable.</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/activepusher/intro.webp' | relative_url }}" alt="A UR10 robot pushes household objects to target regions and table edges using ActivePusher" loading="lazy">
    <figcaption>ActivePusher learns object dynamics from targeted interactions, then uses model uncertainty to construct more reliable manipulation plans.</figcaption>
  </figure>
  <p class="project-lead">
    Planning with learned dynamics can unlock versatile nonprehensile manipulation, but collecting robot data is expensive and prediction errors can compound over long horizons. ActivePusher joins residual physics, uncertainty-aware active learning, and kinodynamic planning in one framework: the robot practices the pushes that teach it the most, then favors high-confidence actions when it is time to act.
  </p>
  <div class="project-callout">
    <p><strong>The result:</strong> more data-efficient model learning and higher planning success in both simulation and real-world pushing tasks—without high-fidelity simulation, large offline datasets, or human demonstrations.</p>
  </div>
</section>

<section aria-labelledby="framework-heading">
  <h2 id="framework-heading">One uncertainty signal, two roles</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/activepusher/framework.webp' | relative_url }}" alt="ActivePusher framework showing active learning and active planning driven by estimated model uncertainty" loading="lazy">
    <figcaption>Estimated model uncertainty guides the system toward informative actions during learning and reliable actions during planning.</figcaption>
  </figure>
  <div class="project-two-column">
    <div class="project-card">
      <h3>Active learning</h3>
      <p>ActivePusher estimates epistemic uncertainty with the neural tangent kernel and uses BAIT to select a batch of skill parameters with high expected information gain. Each real interaction is chosen to improve the dynamics model efficiently.</p>
    </div>
    <div class="project-card">
      <h3>Active planning</h3>
      <p>The same uncertainty estimate biases the kinodynamic planner toward controls in well-explored parts of the skill space. Plans are built from actions the learned model can predict with greater confidence.</p>
    </div>
  </div>
</section>

<section aria-labelledby="region-heading">
  <h2 id="region-heading">Push to region</h2>
  <div class="project-video-grid">
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-region-1.webp' | relative_url }}" aria-label="Push-to-region trial one">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-region-1.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-region trial 1</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-region-2.webp' | relative_url }}" aria-label="Push-to-region trial two">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-region-2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-region trial 2</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-region-3.webp' | relative_url }}" aria-label="Push-to-region trial three">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-region-3.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-region trial 3</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-region-4.webp' | relative_url }}" aria-label="Push-to-region trial four">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-region-4.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-region trial 4</p>
    </div>
  </div>
  <p class="project-lead project-video-description">The robot plans and executes multi-step pushes that move a mustard bottle into a target region while accounting for model uncertainty.</p>
</section>

<section aria-labelledby="edge-heading">
  <h2 id="edge-heading">Push to edge for grasping</h2>
  <div class="project-video-grid">
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-edge-1.webp' | relative_url }}" aria-label="Push-to-edge trial one">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-edge-1.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-edge trial 1</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-edge-2.webp' | relative_url }}" aria-label="Push-to-edge trial two">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-edge-2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-edge trial 2</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-edge-3.webp' | relative_url }}" aria-label="Push-to-edge trial three">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-edge-3.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-edge trial 3</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/activepusher/videos/push-to-edge-4.webp' | relative_url }}" aria-label="Push-to-edge trial four">
        <source src="{{ '/assets/projects/activepusher/videos/push-to-edge-4.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Push-to-edge trial 4</p>
    </div>
  </div>
  <p class="project-lead project-video-description">With obstacles on the table, the planner moves a cracker box to a reachable edge so the robot can complete the task with a grasp.</p>
</section>

<section aria-labelledby="model-heading">
  <h2 id="model-heading">Residual physics for low-data learning</h2>
  <p class="project-lead">
    A coarse analytical pushing model supplies a useful physical prior. A neural network learns only the residual correction between that approximation and observed object motion, retaining physical structure while adapting to object- and contact-specific behavior.
  </p>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/activepusher/active-learning.webp' | relative_url }}" alt="Plots comparing active and random learning with residual-physics and fully learned models" loading="lazy">
    <figcaption>Combining residual physics with active data selection reaches strong predictive performance with substantially fewer interactions than the baselines.</figcaption>
  </figure>
</section>

<section aria-labelledby="planning-heading">
  <h2 id="planning-heading">Uncertainty-aware planning improves execution</h2>
  <p class="project-lead">
    Active sampling steers the planner toward actions with lower model uncertainty. Across planning conditions, this produces more executable plans, improves success, and reduces the gap between planned and observed object motion.
  </p>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/activepusher/active-planning.webp' | relative_url }}" alt="Planning success rate and execution error plots for ActivePusher and baseline methods" loading="lazy">
    <figcaption>Active planning improves success rate and execution accuracy for the learned pushing models.</figcaption>
  </figure>
</section>

<section aria-labelledby="acknowledgments-heading">
  <h2 id="acknowledgments-heading">Acknowledgments</h2>
  <p class="project-lead">This work was supported in part by NSF CRII Grant No. 2451108, an Amazon WPI Robotics Engineering gift, and Worcester Polytechnic Institute funds.</p>
</section>
