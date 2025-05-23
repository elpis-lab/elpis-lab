---
layout: page
permalink: /mqp/
title: Major Qualifying Projects 
description: A list  Current MQPs 
nav: False 
nav_order: 10
---

### MQP#1 Parachute Packing Robot ###
Offered Fall2025 onwards

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mqp/robot_image_packing.jpeg" title="robot_packing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<h2>Motivation&nbsp;</h2>

<p>The US Army is facing a future shortfall of Military Occupational Specialty (MOS) 92R parachute riggers, which will impact the ability to maintain readiness &amp; sustain logistics operations. Due to the life-saving nature of the system, personnel parachute inspection and packing is a methodical process with multiple pre-defined “checkpoints” for inspection of the current packing state for deficiencies before proceeding. While some prior work has been done to investigate the parachute packing process &amp; its automation, efforts have typically been scoped towards improving ergonomics of current processes.</p>

<h2>Overall Project Scope</h2>

<p>The U.S. Soldier Center proposes investigating the parachute packing process to identify how robotics can augment or automate key steps.. Targeted optimization of portions of the parachute packing process can enable rigging personnel to focus on other skilled tasks, reducing overall manpower requirements without decreasing overall safety and readiness. Understanding how humans will interact with automation solutions allows trust in the packing process to be maintained, which is critical for personnel parachute operations.</p>

<h2>Problem description</h2>

<p>Parachute packing is highly complex, making full automation impractical in the short term. Instead, this MQP will focus on automating a single critical step: line stowing. The line stowing process involves organizing, folding, and securing suspension lines to prevent tangling and ensure smooth deployment.</p>

<p>Since <strong>various line stowing techniques</strong> exist (as shown in the videos), this project will <strong>focus on a simplified version</strong>, where the robot must <strong>thread a parachute line through a set of hoops</strong> in a structured manner similar to this <a href="https://youtu.be/xhAcNvjtE5s?si=cMQ1Ss5J-190Y2qz&amp;t=260">video</a>.</p>

<h2>Project Phases</h2>

<h3>Phase 1: Teleoperation System Development</h3>

<ul>
	<li>Develop a <strong>teleoperated robotic system</strong> that can successfully perform line stowing.</li>
	<li>Implement a <strong>6-DOF interface</strong> for intuitive human control of the robotic manipulator.</li>
	<li>Design <strong>specialized fixtures</strong> to assist in the line stowing process.</li>
	<li>Evaluate system feasibility and refine mechanical/robotic components.</li>
	<li>A <strong>robotic arm</strong><a href="https://www.trossenrobotics.com/viperx-300-robot-arm-6dof.aspx"> ViperX 300 6-DOF</a>, will be provided and potential funding for specialized hardware if required.</li>
</ul>

<h3>Phase 2: Autonomous Line Stowing</h3>

<ul>
	<li>Enable the robot to <strong>autonomously stow one or more lines</strong> using the designed fixtures.</li>
	<li>Develop <strong>state estimation</strong> capabilities to track:
	<ul>
		<li><strong>Progress</strong> (number of hoops threaded).</li>
		<li><strong>Failures</strong> (missed stows or misalignment).</li>
		<li><strong>Completion detection</strong> (task success criteria).</li>
	</ul>
	</li>
	<li>Explore <strong>sensor integration (RGB-D, force sensors, or tactile feedback)</strong> to assist in automation.</li>
</ul>

<h2>Sponsoring Organization:</h2>

<p>This project is generously sponsored by the <a href="https://www.army.mil/natick#org-about">U.S. Army Natick Soldier Systems Center (NSSC)</a><strong> </strong><strong>&nbsp;</strong></p>

<h2>Team Members</h2>

<p>A 3 to 5 person team is appropriate for this project. We are primarily seeking&nbsp; students majoring in Robotics Engineering or Mechanical&nbsp; Engineering,&nbsp; though students majoring in Electrical and Computer Engineering or Computer Science may also be a good fit.</p>

If you are interested in participating in this exciting project, please send me an email with your details. We look forward to working with motivated and skilled students to bring this innovative project to life!


### MQP#2 Robotic Solution for Automated Loading of Centrifuges ###
Offered Fall2025

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mqp/aera-theraputics.jpeg" title="robot placing centrifuges" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<p><strong>Problem Statement</strong></p>

<p>Centrifugation is a critical step in numerous experimental assays, from sample preparation to analysis. While many benchtop centrifuges are widely available and cost-effective (~1k), they require scientists to <strong>manually</strong> <strong>load centrifuges</strong> with plates, wait for the centrifuge to spin, and unload plates. <strong>Automated centrifuges</strong>, on the other hand, streamline workflows and integrate seamlessly into automated lab systems, but their prohibitive cost—approximately $60,000 per unit—creates a substantial barrier to adoption among companies already facing high costs for liquid handling and sample transport solutions.</p>

<p>The biotech industry lacks an affordable automated centrifugation option, as well as a means of retrofitting manual centrifuges for automation. This limitation stifles innovation and hinders smaller organizations from leveraging automation to its fullest potential.</p>

<p><strong>Project Description</strong></p>

<p>This MQP aims to develop a robotic system that collaborates with an existing SCARA-type arm such as the <a href="https://www.brooks.com/laboratory-automation/collaborative-robots/preciseflex-400/">PreciseFlex 400</a>, to automate the loading and unloading of microplates in a conventional benchtop <a href="https://ecatalog.corning.com/life-sciences/b2c/US/en/Equipment/Centrifuges/Plate-Spinner-Centrifuges/Axygen%C2%AE-Axyspin-Mini-Plate-Spinner-Centrifuge/p/axygenAxyspinMiniPlateSpinnerCentrifuge">centrifuge</a>.<br />
<br />
The arm can accurately pick and place microplates in a horizontal orientation, but most centrifuges require either vertical insertion or deep placement into the rotor, rendering the existing arm insufficient for the task. This project will focus on designing an additional robotic mechanism that works in conjunction with the arm to successfully load and unload plates into the centrifuge rotor while ensuring precision and reliability.</p>

<p>Specifically this MQP project will design a device that has the following capabilities:</p>

<ul>
	<li>Move plates between a loading nest and the centrifuge rotor.</li>
	<li>Activate and deactivate the centrifuge.</li>
	<li>Allow users to connect the device to a PC via USB, Ethernet, and RS-232.</li>
	<li>Present users with a simple, easy-to-use API in C# and Python that exposes simple commands such as “load”, “unload”, and “spin”.</li>
	<li>Optional: expose the API through a Web interface with a Swagger page</li>
	<li>Detect and report imbalances to the user</li>
	<li>Ensure the safety of users through hardware and software safeguards</li>
</ul>

<p>Additionally, team must produce comprehensive documentation including the following:</p>

<ul>
	<li>Bill of Materials for the device</li>
	<li>Assembly instructions</li>
	<li>Software setup instructions</li>
	<li>API Reference Manual</li>
</ul>

<p><strong>Additional Perks:</strong></p>

<ul>
	<li>You would have the opportunity to tour an active biotech lab</li>
	<li>Network and showcase skills to industry professionals</li>
</ul>

<p><strong>Registering for the MQP</strong></p>

<p>Interested students should email prof. Constantinos Chamzas at <a href="cchamzas@wpi.edu">cchamzas@wpi.edu</a> to declare their interest with subject link <em>MQP<strong>:</strong>Robotic Solution for Automated Loading of Centrifuges</em>. Sending an email as team is encouraged.<br />
&nbsp;</p>

<p><strong>About the Sponsoring Company</strong></p>

<p>This project is generously sponsored by <a href="https://aeratx.com/">Aera Therapeutics.</a> Genetic medicines have the potential to transform the treatment of human disease across a wide range of therapeutic applications. Yet, the broad application of genetic medicines remains limited by today’s available delivery technologies. Aera was founded with a vision to unlock the potential of genetic medicines across a broad range of modalities and therapeutic areas.</p>

<p>With foundational technology developed in the labs of Feng Zhang, Ph.D., of the Broad Institute of MIT and Harvard, and Jason Shepherd, Ph.D., of the University of Utah, Aera was started by a distinguished set of industry leaders and company builders to expand the reach and impact of genetic medicines. Aera’s mission is to harness enabling delivery technologies and precision payloads to develop transformative genetic medicines.</p>

<p>&nbsp;</p>
