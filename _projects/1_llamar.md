---
layout: page
title: Lamarr Rocket at EuRoC 2025
description: Flight software and ground-station work for the TU Wien Space Team's liquid-fuel rocket at EuRoC 2025.
img: # add a thumbnail: place an image in assets/img/ and put its path here, e.g. assets/img/lamarr.jpg
importance: 1
category: engineering
---

The Lamarr project is the TU Wien Space Team's student-built rocket that flies on liquid fuel. Our goal was to design and launch a rocket that could reach around nine kilometers of altitude using an engine we built ourselves. The 2025 rocket was named Hedy, after the Austrian inventor Hedy Lamarr, and we took it to the European Rocketry Challenge (EuRoC) in Portugal, the largest student rocketry competition in Europe.

At the heart of the rocket sits a self-made engine that burns ethanol together with liquid oxygen. It produces about 2,000 newtons of thrust and fires for roughly nine seconds. The body is made almost entirely of carbon fiber to keep it light, with a glass-fiber nose cone on top. Fully fueled the rocket weighs about 25 kilograms and stands 3.7 meters tall. Almost everything on board, from the flight computer to the data logging and the radio link back to the ground, was designed and built by the team itself.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/space_team.jpg" title="Working on the Lamarr rocket in the TU Wien Space Team workshop" class="img-fluid rounded z-depth-1" %}
  </div>
</div>

My part of the project was on the software side, where I worked on the frontend of our ground station. That is the screen the team watches during the countdown and the flight, with live data such as altitude, speed and engine sensor readings arriving over the radio link in real time. The aim was to make all of this easy to read at a glance, so that anyone on the team could quickly tell whether the rocket was healthy before and during the launch.

On October 12, 2025 the rocket lifted off and the flight went really well. Hedy climbed to 5,336 meters and passed the speed of sound at about 1,300 kilometers per hour. That made it the highest flight in its category and the second highest of the whole competition. The recovery did not go perfectly, because the main parachute only opened part of the way, but the rocket still came down in a controlled way and landed with only minor damage. You can read the full story in our [technical report](https://spaceteam.at/wp-content/uploads/2025/10/Technical_Report_Lamarr_EuRoC_2025.pdf), and watch the launch below.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px;">
      <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
        src="https://www.youtube.com/embed/pc_Dvfo6m0g"
        title="Lamarr launch at EuRoC 2025"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen></iframe>
    </div>
  </div>
</div>
