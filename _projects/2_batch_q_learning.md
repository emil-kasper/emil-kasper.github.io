---
layout: page
title: Q-Learning with Batch Sampling
description: A theory and experiment study on whether averaging several samples per update speeds up Q-learning.
img: # add a thumbnail: place an image in assets/img/ and put its path here
importance: 2
category: research
---

Q-learning is a classic way for an agent to learn good decisions by trial and error. In its usual form it updates one value at a time from a single random experience, which makes learning quite noisy. This project asked a simple question. What happens if, instead of relying on one sample, we average several samples together before each update? The idea is that averaging cancels out some of the randomness and points each update more steadily toward the right answer.

I looked at this from two sides, with math and with experiments. On the theory side I wrote the batched update as a step in a well studied family of methods and asked what it does on average. The main finding is that, in expectation, the batched update is just a blend of the ideal update (the one you would make if you knew the true dynamics) and doing nothing at all.

$$
\mathbb{E}[T[q]] = \frac{m}{d} B[q] + \left(1 - \frac{m}{d}\right) q
$$

Here $$m$$ is the batch size and $$d$$ is the number of state-action pairs, so a larger batch puts more weight on the useful part. From there I could show that the method still settles on the optimal values, and that the strength of the pull toward the optimum grows in direct proportion to the batch size.

$$
K_3 = \frac{2m}{d}\left(1 - \sqrt{d}\,\gamma\right)
$$

To check this prediction I ran experiments on FrozenLake, a small grid world where the agent can slip in random directions. I compared batch sizes from 1, the usual single-sample version, up to 32, and measured how quickly the learned values approached the known best solution. The larger batches closed the gap noticeably faster, above all in the early phase of learning, and the effect held across different settings. The honest caveat is that a bigger batch also does more work in each step, so the gain is best read as faster progress per update rather than per unit of raw computation.

The natural next step became a follow-up project on Speedy Q-Learning, a faster relative of ordinary Q-learning that keeps two value estimates and uses the difference between them to take bolder steps. There I combined this speedy update with the same batch-sampling idea and the same stability tracking, and I tested it on more environments, including FrozenLake, Cliff Walking and Taxi. The aim was to see whether the benefit of batching carries over to this stronger method and how stable it stays across different problems.

You can find the code on [GitHub](https://github.com/emil-kasper/Q-Learning-with-Batch-Sampling) and read the full write-up in the [convergence report](https://github.com/emil-kasper/Q-Learning-with-Batch-Sampling/blob/main/Convergence%20Analysis.pdf).
