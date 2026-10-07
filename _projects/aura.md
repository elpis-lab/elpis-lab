---
layout: project
title: AURA
subtitle: Asymptotically Optimal Uncertainty-Robust Replanning Algorithm for Kinodynamic Systems
description: AURA keeps improving kinodynamic plans during execution and precomputes recovery controls to stay on track under motion uncertainty.
permalink: /projects/aura/
og_image: /assets/projects/aura/intro.webp
color_theme: aura
authors:
  - name: Seyedali Golestaneh
    url: https://www.linkedin.com/in/aligolestaneh/
  - name: Zhuoyun Zhong
    url: https://zhuoyunzhong.github.io/
  - name: Donghyung Lee
  - name: Constantinos Chamzas
    url: https://cchamzas.com/
venue: Accepted to IEEE Robotics and Automation Letters (RA-L), 2026
affiliation: Worcester Polytechnic Institute · ELPIS Lab
links:
  - label: URL
    url: https://arxiv.org/abs/2605.27699
    icon: fa-solid fa-link
    external: true
  - label: arXiv
    url: https://arxiv.org/abs/2605.27699
    icon: ai ai-arxiv
    external: true
  - label: PDF
    url: /assets/pdf/golestaneh2026aura.pdf
    icon: fa-regular fa-file-pdf
  - label: Video
    url: https://www.youtube.com/watch?v=bhrmnuMtRw0
    icon: fa-brands fa-youtube
    external: true
  - label: Code
    url: https://github.com/elpis-lab/AURA
    icon: fa-brands fa-github
    external: true
featured_videos:
  - title: Global Replanning Module
    caption: The planner keeps searching the state space during execution and switches to lower-cost trajectories as it finds them.
    src: /assets/projects/aura/videos/global-replanning.mp4
    poster: /assets/projects/aura/videos/global-replanning.webp
    autoplay: true
    highlight: true
  - title: Local Optimization Module
    caption: Optimized controls are precomputed for possible execution outcomes, recoverying the system back toward the nominal trajectory.
    src: /assets/projects/aura/videos/local-optimization.mp4
    poster: /assets/projects/aura/videos/local-optimization.webp
    autoplay: true
    highlight: true
---

<section aria-labelledby="overview-heading">
  <h2 id="overview-heading">Keep the Planner Alive During Execution!</h2>
  <figure class="project-figure" style="max-width: 720px;">
    <img src="{{ '/assets/projects/aura/intro.webp' | relative_url }}" style="border-radius: 36px; padding: 12px;" alt="Open-loop execution of a pushing plan drifting from the planned path compared with AURA replanning and execution" loading="lazy">
    <figcaption>With a short initial planning budget and approximate dynamics, open-loop execution follows a suboptimal plan and drifts away (blue). AURA plans globally and optimizes locally during execution, producing a more optimal trajectory with smaller execution error (orange).</figcaption>
  </figure>
  <p class="project-lead">
    Sampling-based kinodynamic planners handle systems with complex dynamics, but they are usually run offline: the robot waits for a plan, then executes it blindly. Under a limited time budget the plan is often suboptimal, and under model mismatch the system deviates. AURA wraps around any asymptotically optimal planner and puts each execution interval to work, improving the trajectory quality and precomputing corrections beforehand.
  </p>
  <div class="project-callout">
    <p><strong>The result:</strong> Lower-cost trajectories with any initial planning budget, up to 72% less execution deviation than open-loop execution, and up to 50% shorter total task time than receding-horizon and replanning baselines, all without a steering function.</p>
  </div>
</section>

<section aria-labelledby="framework-heading">
  <h2 id="framework-heading">3 Threads, 1 Parallel cycle</h2>
  <figure class="project-figure">
    <img src="{{ '/assets/projects/aura/framework.webp' | relative_url }}" style="border-radius: 30px; padding: 20px;" alt="AURA timeline with an offline planning phase followed by runtime cycles of execution, global replanning, and local optimization" loading="lazy">
    <figcaption>After an offline planning phase, each runtime cycle runs execution, global replanning, and local optimization concurrently, then synchronizes their results before the next control is applied.</figcaption>
  </figure>
  <p class="project-lead">
    AURA is a meta-planner on top of an asymptotically optimal sampling-based planner, such as AO-RRT, AO-EST, or SST. While the system executes the first control, two other modules use the same time window. One searches for a better global plan, the other prepares local recovery controls. At the end of each cycle, AURA evaluates candidate plans from the observed state, chooses the best one, and picks the next control to execute.
  </p>
</section>

<section aria-labelledby="replanning-heading">
  <h2 id="replanning-heading">Global Replanning Module</h2>
  <figure class="project-figure" style="max-width: 620px;">
    <img src="{{ '/assets/projects/aura/global-replanning.webp' | relative_url }}" style="border-radius: 26px; padding: 20px;" alt="Search tree update where unreachable branches are pruned and new samples lead to a lower-cost solution" loading="lazy">
    <figcaption>As the first segment is executed, branches that are no longer reachable to the next state are pruned. Then, planning resumes from the new updated subtree, and any lower-cost solution it finds becomes the new best trajectory.</figcaption>
  </figure>
  <div class="project-two-column">
    <div class="project-card">
      <h3>Pruning stage</h3>
      <p>Once the first control is committed, the next planned state becomes the new root. Only branches that cannot be reached without a steering function are removed; the rest of the exploration progress is kept.</p>
    </div>
    <div class="project-card">
      <h3>Replanning stage</h3>
      <p>As the underlying planner is asymptotically optimal, every extra nodes of search during execution has a chance to find a cheaper path, so the system can start the execution once a feasible plan is found and the rest of the planning can happen online.</p>
    </div>
  </div>
</section>

<section aria-labelledby="optimization-heading">
  <h2 id="optimization-heading">Local Optimization Module</h2>
  <figure class="project-figure" style="max-width: 620px;">
    <img src="{{ '/assets/projects/aura/local-optimization.webp' | relative_url }}" style="border-radius: 26px; padding: 20px;" alt="Batched optimization computing recovery controls from sampled nearby states toward child states in the tree" loading="lazy">
    <figcaption>(a) Applying the nominal control from a perturbed state amplifies the deviation, while a recovery control steers it back toward the nominal plan. (b) AURA samples states around the next planned state and optimizes a recovery control from each sample toward each child in the tree.</figcaption>
  </figure>
  <p class="project-lead">
    Instead of optimizing from the newly observed state like MPC, AURA samples the states the system might end up in and optimizes recovery controls for all of those outcomes in parallel on the GPU while the current action is still executing. When the actual state is observed, it picks the control computed for the nearest sample. The optimization works with any differentiable dynamics, including learned models.
  </p>
  <div class="project-callout">
    <p><strong>Backed by theory:</strong> For trajectories with enough clearance, a recovery segment from any perturbed state back to the nominal successor is guaranteed to exist, and an approximate recovery is enough to keep the robot inside the planned safety margin.</p>
  </div>
</section>

<section aria-labelledby="quality-heading">
  <h2 id="quality-heading">Better Runtime Quality Trajectory</h2>
  <figure class="project-figure" style="max-width: 1080;">
    <img src="{{ '/assets/projects/aura/trajectory-quality.webp' | relative_url }}" style="border-radius: 18px; padding: 15px;" alt="Final trajectory cost for vanilla and AURA versions of AO-RRT, SST, and AO-EST across four dynamical systems" loading="lazy">
    <figcaption>Across a double integrator, a kinematic car, learned pushing dynamics, and a 6D Dubins airplane, AURA consistently returns lower-cost trajectories than the same planner run offline with the same initial planning time.</figcaption>
  </figure>
</section>

<section aria-labelledby="tracking-heading">
  <h2 id="tracking-heading">More Robust Tracking</h2>
  <figure class="project-figure" style="max-width: 1080px;">
    <img src="{{ '/assets/projects/aura/tracking-error.webp' | relative_url }}" style="border-radius: 18px; padding: 15px;" alt="Mean tracking error over ten applied controls for AURA, MPPI, and open-loop execution across five systems and environments" loading="lazy">
    <figcaption>Open-loop execution accumulates tracking error with every control, while AURA keeps tracking error flat and comparable to MPPI across analytical and learned dynamics, under Gaussian noise and in MuJoCo.</figcaption>
  </figure>
  <p class="project-lead">
    Unlike MPPI, which optimizes only after the new state is observed, AURA has its recovery controls ready before the action finishes, so it can correct course immediately at the synchronization step. Moreover, AURA plans globally all the way to the goal, which makes it well suited for long-horizon tasks.
  </p>
</section>

<section aria-labelledby="time-heading">
  <h2 id="time-heading">Faster End-to-End Task Time</h2>
  <figure class="project-figure" style="max-width: 1080px;">
    <img src="{{ '/assets/projects/aura/task-time.webp' | relative_url }}" style="border-radius: 30px; padding: 20px;" alt="Distribution of total task completion time for AURA, restart replanning, MPPI, and Robust-RRT" loading="lazy">
    <figcaption>Including offline planning computation and execution time, AURA reaches the goal faster than restart replanning, MPPI, and Robust-RRT in the more complex systems and in MuJoCo and real-world settings.</figcaption>
  </figure>
  <p class="project-lead">
    Restart replanning throws away the tree after every large deviation, and MPPI cannot find the optimal path or gets trapped in local minima on long tasks. AURA keeps global exploration and local robustness at the same time.
  </p>
</section>

<section aria-labelledby="hyper-heading">
  <h2 id="hyper-heading">Lower Offline Planning is Faster! </h2>
  <figure class="project-figure" style="max-width: 840px;">
    <img src="{{ '/assets/projects/aura/hyperparameters.webp' | relative_url }}" style="border-radius: 18px; padding: 15px;" alt="Car environment with obstacles and a surface plot of task time over offline planning time and maximum control duration" loading="lazy">
    <figcaption>In a car environment where the optimal path threads a narrow passage, the shortest total task time comes from a short offline planning budget and short control durations.</figcaption>
  </figure>
  <p class="project-lead">
    Extra offline planning only pays off if it saves more time than it costs. Because AURA keeps refining during execution, the system is better off once a feasible plan exists and letting replanning find the shortcut on the way.
  </p>
</section>

<section aria-labelledby="simulation-heading">
  <h2 id="simulation-heading">Simulation: Car and Manipulator in MuJoCo</h2>
  <div class="project-video-grid">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/aura/videos/sim-car.webp' | relative_url }}" style="aspect-ratio: 1; object-fit: contain;" aria-label="AURA controlling a MuSHR car in MuJoCo simulation">
        <source src="{{ '/assets/projects/aura/videos/sim-car.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>MuSHR Car</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/aura/videos/sim-pushing.webp' | relative_url }}" style="aspect-ratio: 1; object-fit: contain;" aria-label="AURA pushing an object with a UR10 in MuJoCo simulation">
        <source src="{{ '/assets/projects/aura/videos/sim-pushing.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>UR10 Non-prehensile Pushing</p>
    </div>
  </div>
  <p class="project-lead project-video-description">Uncertainty comes from the mismatch between the simplified dynamics model and the MuJoCo physics, and AURA corrects for it at every step.</p>
</section>

<section aria-labelledby="real-heading">
  <h2 id="real-heading">Real-world pushing with learned dynamics</h2>
  <div class="project-video-grid">
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/aura/videos/real-pushing-1.webp' | relative_url }}" aria-label="AURA real-world pushing trial one">
        <source src="{{ '/assets/projects/aura/videos/real-pushing-1.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Real-world Trial 1</p>
    </div>
    <div class="project-video-card project-video-card--primary">
      <video controls muted loop playsinline preload="metadata" poster="{{ '/assets/projects/aura/videos/real-pushing-2.webp' | relative_url }}" aria-label="AURA real-world pushing trial two">
        <source src="{{ '/assets/projects/aura/videos/real-pushing-2.mp4' | relative_url }}" type="video/mp4">
      </video>
      <p>Real-world Trial 2</p>
    </div>
  </div>
  <p class="project-lead project-video-description">On a real UR10, state is only observed after each push, so AURA's precomputed recovery controls let the robot correct course at every action boundary despite hardware inaccuracies and unmodeled dynamics.</p>
</section>

<section aria-labelledby="acknowledgments-heading">
  <h2 id="acknowledgments-heading">Acknowledgments</h2>
  <p class="project-lead">This work was supported in part by the Amazon WPI RBE Research Award 2025, NSF CRII Grant No. 2451108, and Worcester Polytechnic Institute funds.</p>
</section>
