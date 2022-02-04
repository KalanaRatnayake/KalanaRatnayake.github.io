---
layout: page
title: Masters Research
description: Navigation Planning For A Multi Robot System Exploring An Unknown Environment Supported By Volumetric Data
img: assets/img/projects/msc-project/multi_robot_system_robot.jpg
pdf: assets/pdf/Navigation_Planning_For_A_Multi_Robot_System_Exploring_An_Unknown_Environment_Supported_By_Volumetric_Data.pdf
importance: 1
category: Complete
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/intended_use.jpg" title="high level design of the system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    High level system design
</div>

<h2>Introduction</h2>

<b>Tech Stack:</b> [Robot Operating System (ROS)](https://www.ros.org/), [Octomap Library](https://octomap.github.io/), [Turtlebot system](https://www.turtlebot.com/)

The research project focuses on building a multi robot exploration system to explore unknown environments. The system contains following components,

<ol>
    <li>Client System
        <ol>
            <li>Exploration Module</li>
            <li>Planning Module</li>
            <li>Control Module</li>
            <li>Client Module</li>
        </ol>
    </li>
    <li>Server System</li>
</ol>

<div class="row ml-1 mr-1 p-0">
    <div class="icon" data-toggle="tooltip" title="Thesis report">
        <a href="{{ page.pdf | relative_url }}"><i class="fas fa-file-pdf gh-icon"></i> Download PDF</a>
    </div>
</div>

<br>

<h2>Client System</h2>

This is the system that runs on the robot. This system collects data from the environment and shares them with the server system while navigating and exploring at the same time.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/multi_robot_system_robot.jpg" title="Client System" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Client side system that controls the robot
</div>

<h3>Exploration Module</h3>

The Exploration module analyses a predefined area of the voxel map of the environment by clustering it into groups. This area dimensions can change based on the exploration goals calculated and assigned by the server. Each cluster is evaluated to identify the occupied voxel percentage. If it is above a pre defined threshold, it is considered as an unexplored cluster. Once all the clusters are identified, closest cluster to the robot position is selected as the exploration target. Following image contains the design of this module.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/explorationModuleMulti.jpg" title="Exploration Module" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Exploration Module Design
</div>

<h3>Planning Module</h3>

Planning module functions as the control unit of the system in addition to performing path planning. It requests the exploration goal from the exploration module and also receives the goal calculated by the server through client module. After selecting on goal, it calculates a 2D map of the environment by down projecting the 3D voxel map of the environment. Then it uses the robot's position, selected goal and calculated 2D map to calculate a path. Then it issues control instructions to Control Module to move the robot. Following image explains the design of this module.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/planningModuleMulti.jpg" title="Planning Module" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Planning Module Design
</div>

<h3>Control Module</h3>

This module controls the robot as requested by the Planning Module. Supports 3 basic movements, Forward, Backward and Rotation. In addition to that, also receives SLAM tf data and odometry data from respective ROS nodes to continuously track the position. Following image shows the design of this module.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/controlModuleMulti.jpg" title="Control Module" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Control Module
</div>

<h3>Client Module</h3>

This module communicates with the server. Once it receives a goal from the server, it calculates the area dimensions accordingly and updates other modules Following image shows the design of this module.

<div class="row">
    <div class="col-sm-4 mt-2 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/client_receive.jpg" title="client module receive" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-2 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/client_send.jpg" title="client module send" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Client Module data receiving and sending functionality
</div>

<h2>Server System</h2>

The Server system receives data from all the robots through client modules on each robot. The server merges the maps from all the robots and analyses the derived voxel map of the environment by clustering it into groups. Each cluster is evaluated to identify the occupied voxel percentage. If it is above a pre defined threshold, it is considered as an unexplored cluster. Once all the clusters are identified, clusters are assigned to robots based on the distance between each other. From clusters assigned to a robot, the closes cluster to the robot is selected as the exploration target for that robot and gets transmitted to the robot via control module. Following image shows the design of this system.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/msc-project/server_high_level.jpg" title="Server system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Server System
</div>