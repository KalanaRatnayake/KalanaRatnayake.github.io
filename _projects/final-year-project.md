---
layout: page
title: Undergraduate Research
description: Motion Planner To Explore Unknown Rough Terrain
img: assets/img/projects/final-year-project/data_flow_diagram.png
importance: 2
category: Complete
github: https://github.com/KalanaRatnayake/UnknownTerrainNavigation
pdf: assets/pdf/Motion_Planner_To_Explore_Unknown_Rough_Terrain.pdf
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path=page.img title="high level design of the system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Navigation system design
</div>

<h2>Introduction</h2>

<b>Tech Stack:</b> [Robot Operating System (ROS)](https://www.ros.org/), [Octomap Library](https://octomap.github.io/), [Turtlebot system](https://www.turtlebot.com/)

The research project “Motion planner to explore unknown rough terrain” is focused on building a motion planner for for wheeled robot systems to explore unknown terrains. The system contains 4 components,

<ol>
  <li>Goal Identifier</li>
  <li>Path Planner</li>
  <li>Velocity Controller</li>
  <li>Ground Evaluator</li>
</ol>

<div class="row ml-1 mr-1 p-0">
    <div class="icon" data-toggle="tooltip" title="Thesis report">
        <a href="{{ page.pdf | relative_url }}"><i class="fas fa-file-pdf gh-icon"></i> Download PDF</a>
    </div>
    &ensp;
    <div class="icon" data-toggle="tooltip" title="Code Repository">
        <a href="{{ page.github }}"><i class="fab fa-github gh-icon"></i> Codebase</a>
    </div>
</div>

<br>

<h2>Goal Identifier</h2>

The Goal Identifier subsystem analyses the voxel map of the environment by clustering it into groups. Each group is evaluated to identify the occupied voxel percentage. If it is above a pre defined threshold, it is considered as an unexplored cluster. Once all the clusters are identified, closes cluster to the robot position is selected as the exploration target. Following image contains the design of this subsystem.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/final-year-project/goal_identifier.png" title="Goal Identifier system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Goal Identifier Subsystem
</div>

<h2>Path Planner</h2>

The path planner calculates a 2D map of the environment by down projecting the 3D voxel map of the environment. Then it uses the robot's position, goal position calculated by the Goal Identifier sub system and calculated 2D map to calculate a path. Following image explains the design of this subsystem.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/final-year-project/path_planner.png" title="Goal Identifier system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Path Planner Subsystem
</div>

<h2>Velocity Controller</h2>

This sub system controls the robot as requested by the Path Planner Sub system. Supports 3 basic movements, Forward, Backward and Rotation. Following image shows the design of this sub system.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/final-year-project/velocity_controller.png" title="Goal Identifier system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Goal Identifier Subsystem
</div>


<h2>Ground Evaluator</h2>

This subsystem uses camera images to identify water puddles in the ground. Was not integrated into the final system.