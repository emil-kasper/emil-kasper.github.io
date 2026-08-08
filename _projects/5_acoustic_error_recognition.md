---
layout: page
title: "OMEN: Omission Monitoring via Expectation Networks"
description: Catching missing, unexpected, and context-dependent sounds so a robot knows when to stop.
img: # add a thumbnail: place an image in assets/img/ and put its path here
importance: 5
category: research
---

A robot can hear a crash, but it cannot hear the click that never happened. When a part clicks into place it makes a sound, and when it fails to seat it makes nothing at all. The evidence for that kind of failure is the absence of a sound, and an ordinary sound detector only reacts to what is actually there, so it has nothing to react to. OMEN is a method built to catch exactly these missing sounds, along with two other cases that normal detectors struggle with.

The idea is to learn what each phase of a task should sound like, using only recordings of normal, successful runs. While the robot works, a monitor compares what it expects to hear against what it actually hears, and it does this in both directions. It watches for a sound that should not be there, and for an expected sound that never arrives. If something looks wrong for a few frames in a row, it stops the robot. The alarm level is calibrated so that only a small share of normal runs, five percent by default, ever get interrupted by mistake, and that number is a measured guarantee rather than a hope. The whole thing runs live and only ever uses audio from the past.

The project also ships with its own benchmark, called OMEN-Bench, because existing tests mostly reward a system for reacting at the right moment and rarely punish it for reacting when it should have stayed quiet. OMEN-Bench fills that gap by including sounds that must be ignored, some of them very close to real failures, and by scoring methods on how often they interrupt a normal run. It focuses on three cases that a presence-based detector cannot handle by design. Open-set failures are ones whose sound was never in the training labels. Context-dependent sounds mean different things at different points in the task, so the same noise can be normal in one phase and a fault in another. Omission events are the missing sounds from the start of this description, and they are the main case the project is built around.

The code, a runnable demo, and the full benchmark are on [GitHub](https://github.com/emil-kasper/acoustic-interruption-eval).
