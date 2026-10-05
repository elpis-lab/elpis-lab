---
layout: project
title: Expansion-GRR
subtitle: Efficient Generation of Smooth Global Redundancy Resolution Roadmaps
description: A fast method for building smooth global redundancy resolution roadmaps for consistent and reliable robot teleoperation.
permalink: /projects/expansion-grr/
og_image: /assets/projects/expansion-grr/global-2-2.webp
video_aspect: square
authors:
  - name: Zhuoyun Zhong
    url: https://zhuoyunzhong.github.io/
  - name: Zhi Li
    url: https://wp.wpi.edu/hiro/zhi-jane-li/
  - name: Constantinos Chamzas
    url: https://cchamzas.com/
affiliation: Worcester Polytechnic Institute · ELPIS Lab
venue: Accepted to IROS 2024
links:
  - label: URL
    url: https://ieeexplore.ieee.org/document/10801917
    icon: fa-solid fa-link
    external: true
  - label: arXiv
    url: https://arxiv.org/abs/2405.13770
    icon: ai ai-arxiv
    external: true
  - label: PDF
    url: /assets/pdf/zhong2024-expansion-grr.pdf
    icon: fa-regular fa-file-pdf
  - label: Video
    url: https://www.youtube.com/watch?v=YnLAqy3MtfQ
    icon: fa-brands fa-youtube
    external: true
  - label: Code
    url: https://github.com/elpis-lab/Expansion-GRR
    icon: fa-brands fa-github
    external: true
featured_videos:
  - title: Global consistency
    caption: Expansion-GRR completes a closed task-space loop and returns the robot to its starting configuration.
    src: /assets/projects/expansion-grr/videos/random-circle-expansion-grr.mp4
    poster: /assets/projects/expansion-grr/videos/random-circle-expansion-grr.webp
  - title: Escaping local minima
    caption: The roadmap lets the robot detour through configuration space while following a self-crossing task-space path.
    src: /assets/projects/expansion-grr/videos/self_line_expansion_grr.mp4
    poster: /assets/projects/expansion-grr/videos/self_line_expansion_grr.webp
---

<section aria-labelledby="overview-heading">
  <h2 id="overview-heading">Why global consistency matters</h2>
  <div class="project-two-column project-figure-pair">
    <figure class="project-figure">
      <img src="{{ '/assets/projects/expansion-grr/global-2-1.webp' | relative_url }}" alt="A non-global redundancy resolution returns a three-link manipulator to a different configuration after a closed path" loading="lazy">
      <figcaption><strong>Non-global resolution:</strong> a closed task-space path can end at a different robot configuration.</figcaption>
    </figure>
    <figure class="project-figure">
      <img src="{{ '/assets/projects/expansion-grr/global-2-2.webp' | relative_url }}" alt="A global redundancy resolution returns a three-link manipulator to its original configuration after a closed path" loading="lazy">
      <figcaption><strong>Global resolution:</strong> the same closed path returns the robot to its starting configuration.</figcaption>
    </figure>
  </div>
  <p class="project-lead">
    Redundant robots can reach the same task-space pose with many joint configurations. Local inverse-kinematics methods make these choices one step at a time, which can produce inconsistent motion, singularities, or local minima. Expansion-GRR precomputes a smooth global mapping from task space to configuration space so paths are repeatable, predictable, and ready for real-time use.
  </p>
  <div class="project-callout">
    <p><strong>The result:</strong> GRR roadmaps generated up to two orders of magnitude faster than prior methods, with smoother paths and stronger teleoperation performance.</p>
  </div>
</section>

<section aria-labelledby="method-heading">
  <h2 id="method-heading">Continuity-aware global expansion</h2>
  <p class="project-lead">
    Expansion-GRR starts from selected configuration seeds and grows the configuration-space roadmap in breadth-first order over a discretized task-space roadmap. For each new task-space point, it computes a candidate from multiple solved neighbors, projects that candidate onto the point's self-motion manifold, and retains only edges that pass a recursive continuity check.
  </p>

  <div class="project-method-block">
    <h3>1. Enforce continuity between neighboring configurations</h3>
    <div class="project-two-column project-figure-pair">
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/continuous1.webp' | relative_url }}" alt="A straight path between adjacent points in task space" loading="lazy">
        <figcaption>The end effector moves along a straight segment between adjacent task-space points.</figcaption>
      </figure>
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/continuous2.webp' | relative_url }}" alt="A projected configuration path checked against a straight line in configuration space" loading="lazy">
        <figcaption>Bisected configurations are projected recursively; excessive deviation from the straight configuration-space segment rejects the edge.</figcaption>
      </figure>
    </div>
    <p class="project-lead">The continuity test bisects the task-space and configuration-space segments, projects the intermediate configuration onto the required self-motion manifold, checks its deviation, and repeats recursively to a chosen resolution.</p>
  </div>

  <div class="project-method-block">
    <h3>2. Project from multiple neighbors</h3>
    <div class="project-two-column project-figure-pair">
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/average1.webp' | relative_url }}" alt="A new task-space point and its three neighboring roadmap points" loading="lazy">
        <figcaption>The unsolved point uses multiple nearby points from the task-space roadmap.</figcaption>
      </figure>
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/average2.webp' | relative_url }}" alt="Weighted average of neighboring configurations projected onto a self-motion manifold" loading="lazy">
        <figcaption>Neighboring configurations form a distance-weighted average, which is projected onto the new point's self-motion manifold.</figcaption>
      </figure>
    </div>
    <p class="project-lead">Using all nearby solved configurations reduces the bias and discontinuities that can result from projecting a single neighbor. Closer task-space neighbors receive larger weights.</p>
  </div>

  <div class="project-method-block">
    <h3>3. Seed with a continuous cyclic path</h3>
    <div class="project-two-column project-figure-pair">
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/expansion1.webp' | relative_url }}" alt="Single-seed expansion producing incompatible elbow-up and elbow-down configurations" loading="lazy">
        <figcaption><strong>One seed:</strong> expansion from opposite directions can mix elbow-up and elbow-down solutions, leaving a discontinuity.</figcaption>
      </figure>
      <figure class="project-figure">
        <img src="{{ '/assets/projects/expansion-grr/expansion2.webp' | relative_url }}" alt="Multi-seed expansion from a continuous cyclic path producing a connected roadmap" loading="lazy">
        <figcaption><strong>Multiple seeds:</strong> configurations from a continuous cyclic path guide expansion toward a fully connected solution.</figcaption>
      </figure>
    </div>
    <p class="project-lead">The final roadmap must support cyclic task-space paths. Seeding it with configurations sampled from one continuous cyclic path makes incompatible branches less likely and improves overall connectivity.</p>
  </div>

  <div class="project-callout">
    <p><strong>Global expansion:</strong> a queue traverses the task-space roadmap in breadth-first order. Each unsolved point calls the multi-neighbor projection, then the continuity test determines which configuration-space edges can be safely added.</p>
  </div>
</section>

<section aria-labelledby="random-line-heading">
  <h2 id="random-line-heading">Random line</h2>
  <div class="project-video-grid project-video-grid--three">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random_line_expansion_grr.webp' | relative_url }}" aria-label="Expansion-GRR following a random line">
        <source src="{{ '/assets/projects/expansion-grr/videos/random_line_expansion_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Expansion-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random_line_random_grr.webp' | relative_url }}" aria-label="Random-GRR following a random line">
        <source src="{{ '/assets/projects/expansion-grr/videos/random_line_random_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Random-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random_line_relaxed.webp' | relative_url }}" aria-label="Relaxed IK following a random line">
        <source src="{{ '/assets/projects/expansion-grr/videos/random_line_relaxed.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Relaxed IK</p>
    </div>
  </div>
  <p class="project-lead project-video-description">Expansion-GRR follows the commanded line with a feasible, smooth path. Random-GRR can fail when its roadmap is not sufficiently smooth, while Relaxed IK accumulates more task-space deviation.</p>
</section>

<section aria-labelledby="self-line-heading">
  <h2 id="self-line-heading">Self-crossing line</h2>
  <div class="project-video-grid project-video-grid--three">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/self_line_expansion_grr.webp' | relative_url }}" aria-label="Expansion-GRR following a self-crossing line">
        <source src="{{ '/assets/projects/expansion-grr/videos/self_line_expansion_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Expansion-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/self_line_random_grr.webp' | relative_url }}" aria-label="Random-GRR following a self-crossing line">
        <source src="{{ '/assets/projects/expansion-grr/videos/self_line_random_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Random-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/self_line_relaxed.webp' | relative_url }}" aria-label="Relaxed IK following a self-crossing line">
        <source src="{{ '/assets/projects/expansion-grr/videos/self_line_relaxed.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Relaxed IK</p>
    </div>
  </div>
  <p class="project-lead project-video-description">The global roadmap provides a detour around a difficult configuration-space region; local numerical IK can become trapped in a local minimum.</p>
</section>

<section aria-labelledby="random-circle-heading">
  <h2 id="random-circle-heading">Random circle</h2>
  <div class="project-video-grid project-video-grid--three">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random-circle-expansion-grr.webp' | relative_url }}" aria-label="Expansion-GRR following a random circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/random-circle-expansion-grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Expansion-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random-circle-random-grr.webp' | relative_url }}" aria-label="Random-GRR following a random circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/random-circle-random-grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Random-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/random-circle-relaxed-ik.webp' | relative_url }}" aria-label="Relaxed IK following a random circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/random-circle-relaxed-ik.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Relaxed IK</p>
    </div>
  </div>
  <p class="project-lead project-video-description">Expansion-GRR preserves global consistency over the closed loop, bringing the robot back to the same joint configuration where it started.</p>
</section>

<section aria-labelledby="partial-circle-heading">
  <h2 id="partial-circle-heading">Partially reachable circle</h2>
  <div class="project-video-grid project-video-grid--three">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/partial_circle_expansion_grr.webp' | relative_url }}" aria-label="Expansion-GRR following a partially reachable circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/partial_circle_expansion_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Expansion-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/partial_circle_random_grr.webp' | relative_url }}" aria-label="Random-GRR following a partially reachable circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/partial_circle_random_grr.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Random-GRR</p>
    </div>
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/expansion-grr/videos/partial_circle_relaxed.webp' | relative_url }}" aria-label="Relaxed IK following a partially reachable circle">
        <source src="{{ '/assets/projects/expansion-grr/videos/partial_circle_relaxed.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Relaxed IK</p>
    </div>
  </div>
  <p class="project-lead project-video-description">When part of the command approaches an unreachable or singular region, Expansion-GRR uses roadmap connectivity to recover more reliably.</p>
</section>

<section aria-labelledby="results-heading">
  <h2 id="results-heading">Faster roadmaps, stronger execution</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/expansion-grr/roadmap-quality.webp' | relative_url }}" alt="Table comparing roadmap computation time, connectivity, and smoothness" loading="lazy">
    <figcaption>Across planar and Kinova problems, Expansion-GRR builds highly connected, smooth roadmaps substantially faster than Random-GRR.</figcaption>
  </figure>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/expansion-grr/teleoperation-results.webp' | relative_url }}" alt="Teleoperation experiment results comparing inverse kinematics and GRR methods" loading="lazy">
    <figcaption>The precomputed global roadmap improves teleoperation success and path quality across line and circle tasks.</figcaption>
  </figure>
</section>

<!-- <section aria-labelledby="citation-heading">
  <h2 id="citation-heading">Citation</h2>
  <div class="project-citation">
<pre><code>@inproceedings{zhong2024expansiongrr,
  title     = {Expansion-GRR: Efficient Generation of Smooth Global
               Redundancy Resolution Roadmaps},
  author    = {Zhong, Zhuoyun and Li, Zhi and Chamzas, Constantinos},
  booktitle = {IEEE/RSJ International Conference on Intelligent Robots
               and Systems (IROS)},
  year      = {2024}
}</code></pre>
  </div>
</section> -->
