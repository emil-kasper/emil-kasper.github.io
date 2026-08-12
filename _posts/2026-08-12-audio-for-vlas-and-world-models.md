---
layout: post
title: "Audio for VLAs and world models"
date: 2026-08-12 10:00:00+0200
description: Starting a series on bringing sound into robot learning, beginning with listening for the sounds that never happen.
tags: robotics audio robot-learning
categories: research
---

Most of robot learning is about what a robot sees and does. Vision-language-action models turn camera images and instructions into motions, and world models try to predict what will happen next. Sound is usually left out of this picture. That is a shame, because a lot of what tells you whether a physical task is going well is audible. A part clicks when it seats. A motor strains when it jams. A gripper scrapes when it slips. This is the first entry in a series where I will share my work on bringing audio into robot learning, both for VLAs and for world models. It will grow over time as the project develops.

The starting point is a simple but stubborn problem. A robot can hear a crash, but it cannot hear the click that never happened. When a part fails to seat, the failure makes no sound at all, so the only evidence is the absence of a sound. An ordinary sound detector reacts to what is there, so it has nothing to react to. The first piece of this work, called OMEN, is built around exactly this case. It learns what each phase of a task should sound like from normal runs only, then listens in two directions at once. It watches for a sound that should not be there, and for an expected sound that never arrives. When something looks wrong for a few frames in a row, it stops the robot. The alarm level is calibrated so that only a small share of normal runs, five percent by default, ever get interrupted by mistake.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    <img src="{{ '/assets/img/omen_demo.gif' | relative_url }}" alt="OMEN catching a missing seating click" class="img-fluid rounded z-depth-1" />
  </div>
</div>

The snapshot below shows the idea in one frame. The seating click was due at about 2.9 seconds. The standard detector, in orange, stays flat under its bar the whole time, because nothing wrong actually made a sound. OMEN's missing-sound score, in blue, climbs once the click fails to arrive and crosses its bar shortly after, so the robot stops at 3.04 seconds.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/omen_alarm_moment.png" title="One frame of the demo: the standard detector (orange) never fires, while OMEN's missing-sound score (blue) crosses its bar at 3.04 s and stops the robot." class="img-fluid rounded z-depth-1" %}
  </div>
</div>

Where is this heading? The larger goal is to fold this kind of listening into the models that actually drive robots. A world model that also predicts sound could notice a surprising moment before it turns into a failure. A VLA that can hear could react to feedback that never reaches the camera, like a quiet slip behind the gripper. Those are the directions I want to explore in the next entries, moving from detection towards prediction and control.

The code, a runnable demo, and the benchmark for the OMEN part are on GitHub at [acoustic-interruption-eval](https://github.com/emil-kasper/acoustic-interruption-eval). More soon.
