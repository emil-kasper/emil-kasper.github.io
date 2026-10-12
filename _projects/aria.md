---
layout: page
title: "ARIA: Learning When to Consult Stronger Models"
description: A learned controller that decides when an AI agent should ask a stronger model for help. ICLR 2027 submission.
img: # add a thumbnail: place an image in assets/img/ and put its path here
importance: 0
category: research
---

Modern AI agents often work through long, multi-step tasks such as fixing a codebase or operating a terminal. Running a top-tier model for every single step is expensive. A cheaper model can handle most of the work, and you only call in a stronger model when it really pays off. The hard part is knowing when to ask for help. The usual approach lets the agent judge its own uncertainty, but language models are not good at spotting where their own reasoning goes wrong.

ARIA, which stands for Allocation of Reasoning in Agentic Systems, is a small controller that learns this decision instead of guessing it. At natural decision points in a task, like replanning or delivering a final answer, it looks at simple signals from what has happened so far and chooses one of two actions: stay silent and let the cheaper model continue, or consult the stronger model for guidance. It learns these choices with Monte Carlo reinforcement learning from past runs, rewarding success and penalising the cost of asking. Neither model is retrained, and a single "price of advice" setting slides the whole system between cheap and fast on one end and strong and expensive on the other.

We tested ARIA on three agent benchmarks covering software engineering, terminal tasks, and customer-service style interactions (SWE-bench Verified, Terminal-Bench 2.1, and τ²-bench). It recovers 44 to 81 percent of the performance gap between the cheap and the strong model while spending less than half of what the strong model alone would cost. It came out ahead of ten other strategies, including routing, cascading, and asking at fixed or random moments. The learned policies are small and easy to inspect, so you can actually see when and why the system decides to consult.

This was joint work at ETH Zurich with Pascal Sowietzki, Steffen Holter, Yannick Metz, Raphael Baur, and Prof. Mennatallah El-Assady. You can read the full paper on [arXiv](https://arxiv.org/abs/2610.13870).
