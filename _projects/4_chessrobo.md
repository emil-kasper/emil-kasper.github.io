---
layout: page
title: ChessRobo
description: Teaching an SO-101 robot arm to move chess pieces from natural-language commands (in progress).
img: assets/img/chess_robot.jpg
importance: 4
category: engineering
---

This project teaches an SO-101 robot arm to move chess pieces on a real board from plain language commands such as "move knight from b1 to c3". A camera watches the board and works out where the pieces are, simple rules turn the command into a concrete move, and a vision-language-action model then drives the arm to carry it out.

{% include figure.liquid loading="eager" path="assets/img/chess_robot.jpg" title="The chess-robot setup at the TU Wien Robotics Club" class="img-fluid rounded z-depth-1" %}

The system works as a pipeline. First the perception step uses a single camera to find the squares and read which ones are occupied and in what color, and it keeps track of the board as the game goes on. Then a set of fixed rules figures out the source and target squares and handles captures by splitting them into two steps, first removing the captured piece and then placing the new one. The arm itself is controlled by a pi0.5 model that was fine-tuned with LeRobot, and every real movement passes through a fail-closed safety layer before it reaches the robot. Training runs on a rented GPU while the laptop takes care of the robot, the recording of data, and the evaluation.

The research goal is to compare two ways of making the base policy better after the initial supervised training. The first is residual policy learning, where a small correction is learned on top of the existing policy. The second is human-in-the-loop reinforcement learning, where feedback during operation gradually shapes the behavior. So far the deterministic core, the perception interfaces, the dataset and evaluation tooling, the safety layer, and the pi0.5 training and inference wrappers are all in place. The pi0.5 training has been run from start to finish on a rented GPU, and the piece classifier has been fine-tuned on the real board.

The project is still in progress. What remains is collecting teleoperation demonstrations to learn from, running the full pi0.5 fine-tune on that data, and then carrying out the two reinforcement-learning phases that are the real heart of the comparison. The code lives on [GitHub](https://github.com/emil-kasper/SO101-chess-robot).
