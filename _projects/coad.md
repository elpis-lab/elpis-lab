---
layout: project
title: CoAd
subtitle: Constant-Time Planning for Continuous Goal Manipulation with Compressed Library and Online Adaptation
description: CoAd provides constant-time motion planning across a continuous goal space using certified task coverage regions, a compressed motion library, and fast online adaptation.
permalink: /projects/coad/
og_image: /assets/projects/coad/method-overview.webp
video_fit: contain
authors:
  - name: Adil Shiyas*
    url: https://www.linkedin.com/in/adilshiyas/
  - name: Zhuoyun Zhong*
    url: https://www.linkedin.com/in/zhuoyunzhong/
  - name: Constantinos Chamzas
    url: https://cchamzas.com/
affiliation: Worcester Polytechnic Institute · ELPIS Lab
venue: Under review at ICRA 2027
# After acceptance, replace the venue line above with:
# venue: Accepted to ICRA 2027
links:
  - label: URL
    url: https://arxiv.org/abs/2603.12488
    icon: fa-solid fa-link
    external: true
  - label: arXiv
    url: https://arxiv.org/abs/2603.12488
    icon: ai ai-arxiv
    external: true
  - label: PDF
    url: /assets/pdf/zhong2026coad.pdf
    icon: fa-regular fa-file-pdf
  - label: Video
    url: https://www.youtube.com/watch?v=7beBnjVmmgk
    icon: fa-brands fa-youtube
    external: true
  - label: Code
    url: https://github.com/elpis-lab/CoAd
    icon: fa-brands fa-github
    external: true
---

<section aria-labelledby="overview-heading">
  <h2 id="overview-heading">One workspace, continuously many planning problems</h2>
  <div class="project-video-grid">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/package-task-v2.webp' | relative_url }}" aria-label="A robot repeatedly reaching objects at different poses on a conveyor">
        <source src="{{ '/assets/projects/coad/videos/package-task-v2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Repeated manipulation in a fixed workcell</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/goal-varying-task.webp' | relative_url }}" aria-label="A goal object moving continuously through a fixed manipulation workspace">
        <source src="{{ '/assets/projects/coad/videos/goal-varying-task.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Goal-varying motion planning</p>
    </div>
  </div>
  <p class="project-lead project-video-description">
    Packaging, kitting, and pick-and-place applications repeatedly solve nearly the same motion-planning problem. The static workspace is unchanged, but the goal object can occupy infinitely many poses in a continuous task space. Planning from scratch wastes this structure; storing a separate path for every pose is impossible.
  </p>
  <div class="project-callout">
    <p><strong>CoAd</strong> turns this infinite family into a finite, coverage-certified representation, compresses the resulting motion library, and answers each online query with constant-time retrieval followed by lightweight goal adaptation.</p>
  </div>
</section>

<section aria-labelledby="coverage-heading">
  <h2 id="coverage-heading">Discretize a continuous task space with coverage guarantees</h2>
  <div class="project-video-grid">
    <div class="project-video-card">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/task-space-region.webp' | relative_url }}" aria-label="Task Space Region animation showing valid end-effector goals for an object pose">
        <source src="{{ '/assets/projects/coad/videos/task-space-region.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Task Space Region: valid end-effector poses for one object pose</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/task-coverage-region-v2.webp' | relative_url }}" aria-label="Task Coverage Region animation showing object poses sharing a fixed end-effector goal">
        <source src="{{ '/assets/projects/coad/videos/task-coverage-region-v2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Task Coverage Region: object poses sharing one end-effector goal</p>
    </div>
  </div>
  <p class="project-lead project-video-description">
    A Task Space Region describes all end-effector poses that can complete a task for one object pose. CoAd inverts that relationship: a <strong>Task Coverage Region (TCR)</strong> describes the continuous set of object poses that can share one fixed end-effector goal. Finite TCR cells cover the bounded task domain and provide direct indexing at query time.
  </p>
  <figure class="project-figure project-figure--compact">
    <img src="{{ '/assets/projects/coad/task-coverage-regions.webp' | relative_url }}" alt="Diagram relating Task Space Regions, their intersections, Task Coverage Regions, and finite task-space cells" loading="lazy">
    <figcaption>Overlapping Task Space Regions reveal shared goals; Task Coverage Regions then divide the continuous domain into finitely indexed cells.</figcaption>
  </figure>
</section>

<section aria-labelledby="method-heading">
  <h2 id="method-heading">Plan a few roots. Adapt them to cover the rest.</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/coad/method-overview.webp' | relative_url }}" alt="CoAd pipeline from task-space discretization and offline library construction to constant-time online retrieval and adaptation" loading="lazy">
    <figcaption>Offline, CoAd plans root motions and verifies their adaptations across neighboring TCRs. Online, a query is indexed, retrieved, and adapted to its exact goal.</figcaption>
  </figure>
  <div class="project-two-column">
    <div class="project-card">
      <h3>Coverage-preserving compression</h3>
      <p>CoAd stores root paths only for selected TCRs. A root is adapted to nearby regions and each candidate is checked offline for goal satisfaction and collision avoidance. Successful adaptations replace many individually stored plans without sacrificing coverage.</p>
    </div>
    <div class="project-card">
      <h3>Constant-time online query</h3>
      <p>The sensed object pose maps directly to a TCR index. A hash lookup retrieves the associated root motion and goal, after which a fixed-cost adapter produces the final trajectory. Expensive planning and verification remain offline.</p>
    </div>
  </div>
</section>

<section aria-labelledby="adaptation-heading">
  <h2 id="adaptation-heading">Three lightweight adaptation choices</h2>
  <div class="project-video-grid project-video-grid--three">
    <div class="project-card">
      <h3>Linear interpolation</h3>
      <p>Connects the root path endpoint to the queried goal. It is the fastest option, with planning times around 50–90 microseconds in the reported experiments.</p>
    </div>
    <div class="project-card">
      <h3>Dynamic Movement Primitives</h3>
      <p>Retargets the full motion while preserving its qualitative shape. DMPs often produce the shortest paths, trading some compression and query speed for path quality.</p>
    </div>
    <div class="project-card">
      <h3>Simple trajectory optimization</h3>
      <p>Warm-starts a fixed-size convex refinement from the root motion, balancing velocity, acceleration, and deviation from the stored path.</p>
    </div>
  </div>
</section>

<section aria-labelledby="experiments-heading">
  <h2 id="experiments-heading">Experiment setup</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/coad/experiment-environments.webp' | relative_url }}" alt="Panda and Fetch robots evaluated in Conveyor, All Stable, Cage, Shelf, and Microwave environments" loading="lazy">
    <figcaption>Panda (top) and Fetch (bottom) are evaluated in Conveyor, All Stable, Cage, Shelf, and Microwave environments.</figcaption>
  </figure>
  <p class="project-lead">
    The simulation study spans 7-DOF and 8-DOF manipulators across five environments with continuous position, orientation, stable-placement, height, and articulated-door variations. CoAd is compared with full motion libraries, online RRT-Connect variants, and the experience-based ERT-Connect planner.
  </p>
</section>

<section aria-labelledby="simulation-heading">
  <h2 id="simulation-heading">Simulation: conveyor task</h2>
  <div class="project-method-block">
    <h3>Planning baselines</h3>
    <div class="project-video-grid">
      <div class="project-video-card">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/sim-rrt-connect.webp' | relative_url }}" aria-label="RRT-Connect solving the conveyor task in simulation">
          <source src="{{ '/assets/projects/coad/videos/sim-rrt-connect.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>RRT-Connect</p>
      </div>
      <div class="project-video-card">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/sim-ert-connect.webp' | relative_url }}" aria-label="ERT-Connect solving the conveyor task in simulation">
          <source src="{{ '/assets/projects/coad/videos/sim-ert-connect.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>ERT-Connect</p>
      </div>
    </div>
  </div>
  <div class="project-method-block">
    <h3>CoAd adaptations</h3>
    <div class="project-video-grid project-video-grid--three">
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/sim-coad-li.webp' | relative_url }}" aria-label="CoAd with linear interpolation solving the conveyor task in simulation">
          <source src="{{ '/assets/projects/coad/videos/sim-coad-li.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-LI</p>
      </div>
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/sim-coad-dmp.webp' | relative_url }}" aria-label="CoAd with Dynamic Movement Primitives solving the conveyor task in simulation">
          <source src="{{ '/assets/projects/coad/videos/sim-coad-dmp.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-DMP</p>
      </div>
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/sim-coad-sto.webp' | relative_url }}" aria-label="CoAd with simple trajectory optimization solving the conveyor task in simulation">
          <source src="{{ '/assets/projects/coad/videos/sim-coad-sto.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-STO</p>
      </div>
    </div>
  </div>
</section>

<section aria-labelledby="real-heading">
  <h2 id="real-heading">Real-world validation</h2>
  <div class="project-method-block">
    <h3>Planning baselines</h3>
    <div class="project-video-grid">
      <div class="project-video-card">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/real-rrt-connect.webp' | relative_url }}" aria-label="RRT-Connect on the real UR10 manipulation task">
          <source src="{{ '/assets/projects/coad/videos/real-rrt-connect.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>RRT-Connect</p>
      </div>
      <div class="project-video-card">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/real-lightning.webp' | relative_url }}" aria-label="Lightning on the real UR10 manipulation task">
          <source src="{{ '/assets/projects/coad/videos/real-lightning.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>Lightning</p>
      </div>
    </div>
  </div>
  <div class="project-method-block">
    <h3>CoAd adaptations</h3>
    <div class="project-video-grid project-video-grid--three">
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/real-coad-li.webp' | relative_url }}" aria-label="CoAd with linear interpolation on the real UR10 manipulation task">
          <source src="{{ '/assets/projects/coad/videos/real-coad-li.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-LI</p>
      </div>
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/real-coad-dmp.webp' | relative_url }}" aria-label="CoAd with Dynamic Movement Primitives on the real UR10 manipulation task">
          <source src="{{ '/assets/projects/coad/videos/real-coad-dmp.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-DMP</p>
      </div>
      <div class="project-video-card project-video-card--primary">
        <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/coad/videos/real-coad-sto.webp' | relative_url }}" aria-label="CoAd with simple trajectory optimization on the real UR10 manipulation task">
          <source src="{{ '/assets/projects/coad/videos/real-coad-sto.mp4' | relative_url }}" type="video/mp4">
        </video>
        <p>CoAd-STO</p>
      </div>
    </div>
  </div>
  <p class="project-lead project-video-description">
    The compressed library is built in simulation and transferred directly to a physical UR10. AprilTag perception estimates each new object pose, and CoAd retrieves and adapts a verified motion without replanning from scratch. Across 100 trials, all three CoAd variants achieve 100% success with predictable query time and competitive path quality.
  </p>
</section>

<section aria-labelledby="results-heading">
  <h2 id="results-heading">Coverage, compression, and online performance</h2>
  <div class="project-method-block">
    <h3>Compressed plan libraries</h3>
    <p class="project-lead">CoAd-LI and CoAd-STO provide the strongest and most consistent compression, reducing the number of stored paths by roughly 63–99% and 71–99%, respectively. CoAd-DMP often produces higher-quality paths but stores more roots in tightly constrained environments.</p>
    <figure class="project-figure project-figure--compact">
      <img src="{{ '/assets/projects/coad/table1-compression.png' | relative_url }}" alt="Table comparing library compression, adaptation time, path quality, and stored library size across CoAd variants" loading="lazy">
      <figcaption>Plan-library results. OOM indicates that the full library or DMP representation exceeded the available 32 GB of memory.</figcaption>
    </figure>
  </div>
  <div class="project-method-block">
    <h3>Success rate and path quality</h3>
    <p class="project-lead">All available CoAd variants achieve 100% success across the evaluated tasks, while planning-from-scratch and experience-based baselines lose reliability in constrained scenes. CoAd-DMP generally yields the shortest simulated paths, while CoAd-LI gives the best real-world path quality among the compressed variants.</p>
    <figure class="project-figure">
      <img src="{{ '/assets/projects/coad/table2-path-quality.png' | relative_url }}" alt="Table comparing success rate and joint-space path quality for planning baselines and CoAd variants" loading="lazy">
      <figcaption>Online planning success and joint-space path quality over 1,000 random simulation queries per setting and 100 real-world trials.</figcaption>
    </figure>
  </div>
  <div class="project-method-block">
    <h3>Fast and predictable online queries</h3>
    <figure class="project-figure">
      <img src="{{ '/assets/projects/coad/planning-time.png' | relative_url }}" alt="Log-scale comparison of planning-time distributions across all methods and environments" loading="lazy">
      <figcaption>Planning-time distributions on a logarithmic scale across all simulation environments and the real UR10 experiment.</figcaption>
    </figure>
    <p class="project-lead">CoAd-LI consistently answers queries in approximately 50–90 microseconds. CoAd-DMP and CoAd-STO remain in the millisecond range, with substantially smaller timing variance than online baselines—empirical support for the framework’s constant-time online complexity.</p>
  </div>
</section>
