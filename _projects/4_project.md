---
layout: page
title: Cognitive Prosthesis for Goal Achievement
description: Incorporating dynamic priorities in classification of tasks to optimize current model.
img: assets/img/proj4_title.jpg
importance: 2
category: Data Science & Machine Learning
---

I first create a visualization of the MDP model that <a href="https://www.researchgate.net/publication/318958840_Cognitive_Prostheses_for_Goal_Achievement">Lieder, Chen, Krueger, and Griffiths (2019)</a> used to compute optimal incentives for to-do list gamification assuming that there are five to-dos that take 5,10,15,20,25 minutes would consist of 32 states. The figure below is the state diagram of the to-do list gamification:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj4_title.jpg" title="State Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    State Diagram of MDP model for to-do list gamification.
</div>

The model consisted of 32 states. The actions at every state comprises doing one of the five to-do tasks or doing nothing i.e. if the agent is in a certain state where he has done a certain set of tasks and is trying to repeat a previously done task he will stay in the same state. Also, there is an exit state where the user can go to from any state for termination when the user loses motivation and leaves a task in between or stops doing tasks.

The rewards i.e. number of points assigned to each task was computed by optimal gamification, which takes into account the time required to complete the to-do and the value of the goals that each task contributes and how much it contributes to it. According to the optimal reward function derived in the paper:

The reward function after inclusion of pseudo rewards, has the original reward and difference in state value functions of next state and current state. Hence, even though the negative reward or cost of the 25-minute task may be the highest, the difference in state value of the next state and current state in this case is also the highest. This is because the state values depend upon the percentage of task left to achieve the end goal i.e. in this case the $20 reward. 

Further, to extend the current research, I proposed that I would include further priority classification of tasks i.e. we could make five groups of priority where the first group or GROUP A would be the tasks of highest priority, the second group or GROUP B would be tasks of comparatively less priority as compared to tasks of GROUP A but are tasks of importance. GROUP C would comprise tasks that the user wants to do but can be done at a later time. GROUP D would consist of tasks that are important but can be delegated to other people to complete. Finally, GROUP E would have unimportant tasks. 