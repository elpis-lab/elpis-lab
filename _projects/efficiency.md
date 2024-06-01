---
layout: page
title:  Planning Efficiency 
description: Enchance planners efficiency through algorithmic improve-ments and learning methods.
img: assets/img/research/efficient_planning.jpg
importance: 1
related_publications: true
category : Research Areas
---

To deploy robots in time constrained applications, effi-
cient robot motion trajectory computation is crucial. Prob-
lems such as picking an object from a deep shelf (Fig. 1)
are still quite challenging for planners due to the narrow
areas the robot needs to traverse, often requiring minutes
of computation. When solving a new task, drawing knowl-
edge from past experiences can significantly reduce the
Fig. 1: A Fetch robot solving three challenging object pick- required planning time. However, leveraging this experi-
ing tasks in constrained environments.
ence is not trivial. On one hand, despite the different size
of the workspaces, the motion planning problems P1 and P2 of Fig. 1 have similar solution paths,
due to the shared local structure of their workspaces. On the other hand, visually similar workspaces
such as P2 and P3 can have completely different solution paths due to slight start/goal changes, or
different obstacle arrangements. Such subtle differences render the mapping from problem descrip-
tions (workspace, start, goal) to high dimensional paths discontinuous. Learning mappings that
leverage local structure and are sensitive to the discontinuous nature of the path planning problem
is challenging even for state-of-the art machine learning techniques.
To address this challenge, I proposed a new framework for learning sampling distributions to
guide sampling-based motion planners – a widely used class of planners that discover solution
paths through sampling. By combining non parametric learning methods (based on information
1Constantinos Chamzas | Research Statement
retrieval) and local geometric decompositions, I successfully handled the shared structure and
discontinuity problem, resulting in an order of magnitude performance improvement over competing
learning methods. I also proposed a way to learn retrieval functions, specific for motion planning
problems, utilizing contrastive learning in a self supervised training scheme. My proof-of-concept
work with a high degree of freedom (high-DoF) manipulator in a 2D geometric environment [1]
was featured in the research media news outlet TechExplore1 . Using more efficient retrieval and
data generation techniques, I successfully scaled this framework to real robots operating in sensed
3D environments [2], as shown in Fig. 2. This work was recognized with a nomination for the Best
Paper Award in Cognitive Robotics in ICRA2021. Finally, by learning the retrieval function [3] this
framework achieved state-of-the art generalizability across a wide range of scenarios. Most notably,
it improved the performance of planners in unseen scenarios, such as picking objects from tables
using experiences only from bookshelf scenarios. Through this line of research, which is released as
an open source project2 , I acquired a deep understanding of the challenges in integrating planning
algorithms with modern machine learning methods in the context of robotics, and developed a basic
set of strategies to address them.
I have used my expertise in this area in collaboration with other researchers to improve other
aspects of motion planners that incorporate learning. These collaborations included a path defor-
mation method for one shot generalization [4], leveraging past experiences for constrained motion
planning [5], constructing differentiable surrogates for (non-differentiable) planners to optimize the
respective learned sampling distributions [6] and tuning hyperparameters of planners [7].
Further, my experience in this field led me to observe
that properly evaluating new planners remains a challenge.
Researchers often create their own ad hoc benchmarking
datasets, a process which is time consuming and bias prone.
The advent of learning based planners has exacerbated this
problem because they rely on datasets both for learning
and evaluation. In an effort to create community-accepted
datasets and benchmarks, I led a research team with mem-
bers from several universities and proposed a benchmarking
dataset generator [8] along with several challenging motion
Fig. 2: a) Real robot workspace. b) Internal workspace
planning problems. This collaboration rekindled interest in representation, from Vicon cameras (green boxes) or
planner evaluation, which I fostered by co-organizing a suc- robot’s camera (orange voxels).
cessful workshop3 on the topic at in IROS 2022. The widespread participation and positive feedback
convinced me to continue hosting these workshops with the ultimate goal of developing community
wide benchmarks for motion planning.


<div class="publications">
<left> <h2><span style="color: var(--global-theme-color)"> Relevant Publications </span></h2> </left>
{% bibliography -f papers -q @*[keyword1=efficiency] || @*[keyword2=efficiency] || @*[keyword3=efficiency] %}
</div>