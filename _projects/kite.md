---
layout: project
title: Terminal Matters
subtitle: Kinodynamic Planning with a Terminal Cost and Learned Uncertainty in Belief State-Cost Space
description: KiTe explicitly optimizes terminal-state quality and goal-reaching reliability in kinodynamic and belief-space planning.
permalink: /projects/kite/
og_image: /assets/projects/kite/pushing-intro.webp
video_fit: contain
authors:
  - name: Zhuoyun Zhong
    url: https://zhuoyunzhong.github.io/
  - name: Seyedali Golestaneh
    url: https://www.linkedin.com/in/aligolestaneh/
  - name: Constantinos Chamzas
    url: https://cchamzas.com/
affiliation: Worcester Polytechnic Institute · ELPIS Lab
venue: Under review at IEEE Transactions on Robotics (T-RO)
# After acceptance, replace the venue line above with:
# venue: Accepted by IEEE Transactions on Robotics (T-RO), 2026
links:
  - label: URL
    url: https://arxiv.org/abs/2605.09046
    icon: fa-solid fa-link
    external: true
  - label: arXiv
    url: https://arxiv.org/abs/2605.09046
    icon: ai ai-arxiv
    external: true
  - label: PDF
    url: /assets/pdf/zhong2026kite.pdf
    icon: fa-regular fa-file-pdf
  - label: Video
    url: https://www.youtube.com/watch?v=XgUaRy2WUow
    icon: fa-brands fa-youtube
    external: true
  - label: Code
    url: https://github.com/elpis-lab/KiTe
    icon: fa-brands fa-github
    external: true
featured_videos:
  - title: Car parking with terminal cost
    caption: Terminal cost enables continuous optimization after finding a feasible solution.
    src: /assets/projects/kite/videos/7_car_KiTe.mp4
    poster: /assets/projects/kite/videos/7_car_KiTe.webp
  - title: Planar pushing with learned dynamics
    caption: Planning with learned dynamics and uncertainty to push an object reliably toward the goal.
    src: /assets/projects/kite/videos/11_perform_push_real_trash_truck_1.mp4
    poster: /assets/projects/kite/videos/11_perform_push_real_trash_truck_1.webp
---

<section aria-labelledby="overview-heading">
  <h2 id="overview-heading">Reaching the goal is not the whole objective</h2>
  <div class="project-two-column project-figure-pair">
    <figure class="project-figure">
      <img src="{{ '/assets/projects/kite/pushing-intro.webp' | relative_url }}" alt="Two pushing trajectories trading running cost against terminal uncertainty" loading="lazy">
      <figcaption>A shorter pushing trajectory can finish with greater uncertainty, while a longer trajectory can reach the goal more reliably.</figcaption>
    </figure>
    <figure class="project-figure">
      <img src="{{ '/assets/projects/kite/car-intro.webp' | relative_url }}" alt="A car choosing between two feasible parking goals with different preferences" loading="lazy">
      <figcaption>Multiple goal regions may be feasible, but a terminal cost can encode which final state is preferable.</figcaption>
    </figure>
  </div>
  <p class="project-lead">
    Sampling-based kinodynamic planners usually optimize costs accumulated along a trajectory and treat goal arrival as a feasibility check. Terminal-state quality can matter just as much: a goal may be preferable, closer to its center, or substantially more reliable under uncertainty. KiTe augments AO-RRT with an explicit terminal cost so the planner optimizes both how it moves and where its trajectory ends.
  </p>
  <div class="project-callout">
    <p><strong>KiTe:</strong> <strong>Ki</strong>nodynamic planning with a <strong>Te</strong>rminal cost. The formulation preserves asymptotic optimality while supporting deterministic state space, belief space, goal preference, and goal-reaching reliability.</p>
  </div>
</section>

<section aria-labelledby="objective-heading">
  <h2 id="objective-heading">Add terminal quality to the planning objective</h2>
  <div class="project-two-column project-figure-pair">
    <figure class="project-figure">
      <img src="{{ '/assets/projects/kite/regular-terminal-cost.webp' | relative_url }}" alt="State-space objective combining running cost and terminal cost" loading="lazy">
      <figcaption>In state space, KiTe combines trajectory running cost with a cost evaluated at the terminal state.</figcaption>
    </figure>
    <figure class="project-figure">
      <img src="{{ '/assets/projects/kite/belief-terminal-cost.webp' | relative_url }}" alt="Belief-space objective combining running cost and terminal belief cost" loading="lazy">
      <figcaption>In belief space, the terminal term evaluates the final state distribution rather than only its mean.</figcaption>
    </figure>
  </div>
  <div class="project-two-column">
    <div class="project-card">
      <h3>AO-RRT with a terminal cost</h3>
      <p>KiTe searches in the augmented state-cost space and updates the best cost using both accumulated running cost and terminal-state cost. The paper proves that AO-RRT remains asymptotically optimal under this augmented objective.</p>
    </div>
    <div class="project-card">
      <h3>Belief-space extension</h3>
      <p>The same construction applies when each planning state is a belief distribution. KiTe propagates mean and covariance and preserves asymptotic optimality with respect to the belief-space objective.</p>
    </div>
  </div>
</section>

<section aria-labelledby="reliability-heading">
  <h2 id="reliability-heading">A principled objective for goal-reaching reliability</h2>
  <figure class="project-figure project-figure--compact">
    <img src="{{ '/assets/projects/kite/goal-probability-bound.webp' | relative_url }}" alt="Lower bound on goal-reaching probability expressed using Wasserstein distance" loading="lazy">
    <figcaption>Reducing the 2-Wasserstein distance between the terminal belief and the goal Dirac measure improves a lower bound on the probability of reaching the goal region.</figcaption>
  </figure>
  <p class="project-lead">
    Instead of imposing only a hard terminal probability threshold, KiTe directly improves terminal reliability. The Wasserstein terminal cost jointly captures distance to the goal and state uncertainty, encouraging solutions whose final belief is concentrated inside the goal region.
  </p>
</section>

<section aria-labelledby="flappy-heading">
  <h2 id="flappy-heading">Flappy Bird</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/kite/flappy-bird-results.webp' | relative_url }}" alt="Flappy Bird trajectories comparing KiTe with kinodynamic planning baselines" loading="lazy">
    <figcaption>After finding a feasible trajectory, KiTe continues improving the terminal state toward the center of the goal while reducing total cost.</figcaption>
  </figure>
</section>

<section aria-labelledby="car-heading">
  <h2 id="car-heading">Car parking</h2>
  <div class="project-video-grid">
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/7_car_GBT.webp' | relative_url }}" aria-label="Gaussian Belief Tree car parking result">
        <source src="{{ '/assets/projects/kite/videos/7_car_GBT.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Gaussian Belief Tree baseline</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/7_car_KiTe.webp' | relative_url }}" aria-label="KiTe car parking result">
        <source src="{{ '/assets/projects/kite/videos/7_car_KiTe.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>KiTe</p>
    </div>
  </div>
  <p class="project-lead project-video-description">The baseline tends to select the nearest feasible parking region and stops refining after satisfying the goal constraint. KiTe selects the preferred open-space goal and continues improving the terminal belief.</p>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/kite/car-results.webp' | relative_url }}" alt="Car parking trajectories and terminal belief distributions" loading="lazy">
    <figcaption>KiTe accounts for both goal preference and terminal uncertainty in belief-space car parking.</figcaption>
  </figure>
</section>

<section aria-labelledby="learning-heading">
  <h2 id="learning-heading">Learning belief dynamics from interactions</h2>
  <div class="project-video-grid">
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/8_learn_dynamics_sim_chef_can.webp' | relative_url }}" aria-label="Collecting simulated pushing data with a chef can">
        <source src="{{ '/assets/projects/kite/videos/8_learn_dynamics_sim_chef_can.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Chef can data collection</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/8_learn_dynamics_sim_mustard_bottle.webp' | relative_url }}" aria-label="Collecting simulated pushing data with a mustard bottle">
        <source src="{{ '/assets/projects/kite/videos/8_learn_dynamics_sim_mustard_bottle.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Mustard bottle data collection</p>
    </div>
  </div>
  <p class="project-lead project-video-description">For contact-rich systems without analytical uncertainty models, interaction data provides the transitions needed to learn belief dynamics.</p>
  <figure class="project-figure project-figure--compact">
    <img src="{{ '/assets/projects/kite/learned-belief-dynamics.webp' | relative_url }}" alt="Neural belief dynamics model with mean and uncertainty prediction heads" loading="lazy">
    <figcaption>A neural network trained with negative log-likelihood predicts both the mean local transition and process uncertainty for belief propagation during planning.</figcaption>
  </figure>
</section>

<section aria-labelledby="simulation-heading">
  <h2 id="simulation-heading">Planar pushing in simulation</h2>
  <div class="project-video-grid">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/10_perform_push_sim_chef_can.webp' | relative_url }}" aria-label="KiTe pushing a chef can in simulation">
        <source src="{{ '/assets/projects/kite/videos/10_perform_push_sim_chef_can.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Chef can</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/10_perform_push_sim_mustard_bottle.webp' | relative_url }}" aria-label="KiTe pushing a mustard bottle in simulation">
        <source src="{{ '/assets/projects/kite/videos/10_perform_push_sim_mustard_bottle.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Mustard bottle</p>
    </div>
  </div>
</section>

<section aria-labelledby="real-heading">
  <h2 id="real-heading">Real-world planar pushing</h2>
  <div class="project-video-grid">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/11_perform_push_real_cracker_box_1.webp' | relative_url }}" aria-label="KiTe real-world cracker box trial one">
        <source src="{{ '/assets/projects/kite/videos/11_perform_push_real_cracker_box_1.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Cracker box trial 1</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/11_perform_push_real_cracker_box_2.webp' | relative_url }}" aria-label="KiTe real-world cracker box trial two">
        <source src="{{ '/assets/projects/kite/videos/11_perform_push_real_cracker_box_2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Cracker box trial 2</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/11_perform_push_real_trash_truck_1.webp' | relative_url }}" aria-label="KiTe real-world trash truck trial one">
        <source src="{{ '/assets/projects/kite/videos/11_perform_push_real_trash_truck_1.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Trash truck trial 1</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/kite/videos/11_perform_push_real_trash_truck_2.webp' | relative_url }}" aria-label="KiTe real-world trash truck trial two">
        <source src="{{ '/assets/projects/kite/videos/11_perform_push_real_trash_truck_2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Trash truck trial 2</p>
    </div>
  </div>
  <p class="project-lead project-video-description">Across simulated and real-world objects, KiTe uses learned belief dynamics to favor trajectories with smaller terminal uncertainty and stronger goal-reaching reliability.</p>
</section>
