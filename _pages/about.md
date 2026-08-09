---
layout: about
title: about
permalink: /
subtitle: Computer Science @ ETH Zurich · Research Fellow @ ETH Zurich.

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: >
    <p>ETH Zurich, Zurich, Switzerland</p>
    <p><a href="mailto:kaspere@ethz.ch">kaspere@ethz.ch</a></p>

selected_papers: false # set to true once you add papers to _bibliography/papers.bib marked selected={true}
social: false # set to true to show social icons at the bottom of the page

announcements:
  enabled: false # news is shown via the expandable section in the page body instead

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

<style>
  /* Name heading: normal weight, no uppercase */
  .post-header .post-title,
  .post-header .post-title span { font-weight: 400 !important; text-transform: none !important; }
  /* News expander button */
  details.news-expander summary { cursor: pointer; display: inline-block; padding: 0.4rem 0.9rem; border: 1px solid currentColor; border-radius: 6px; list-style: none; user-select: none; }
  details.news-expander summary::-webkit-details-marker { display: none; }
  details.news-expander summary::after { content: " ▸"; }
  details.news-expander[open] summary::after { content: " ▾"; }
  .news-row { display: flex; gap: 0.9rem; margin: 0.7rem 0; }
  .news-date { white-space: nowrap; opacity: 0.65; min-width: 7em; }
  @media (max-width: 576px) { .news-row { flex-direction: column; gap: 0.1rem; } }
  /* Keep the bio text in its own column so it never flows underneath the profile image */
  @media (min-width: 576px) {
    .post > article > .clearfix { display: flow-root; }
  }
</style>

I'm a Computer Science student at [ETH Zurich](https://ethz.ch/), interested in reinforcement learning, robot learning, and explainability.

Before that, I completed my Bachelor's at [TU Wien](https://tuwien.ac.at/) in Vienna, including an additional one-year honours track that let me focus on machine learning. During that time, I spent a year as a Software Engineer at Siemens Mobility, contributing to a testing framework for the European Train Control System (ETCS) and its autonomous train operation (ATO) mode.

In parallel, I carried out reinforcement-learning research as an undergraduate researcher in TU Wien's Machine Learning Research Unit under Prof. Clemens Heitzinger, where I studied the convergence and stability of Q-Learning and Speedy Q-Learning. I also worked as a teaching assistant at the Institute for Human-Centered Technology, helped build rockets with the TU Wien Space Team, and was involved in policy-making for digital technologies.

Currently, I am pursuing a Master's in Computer Science at ETH Zurich and working as a Research Fellow at the [IVIA Lab](https://ivia.ch/) on agency delegation and human–AI collaboration in shared-initiative settings. I am also involved in the [TU Wien Robotics Club](https://www.tuwrc.at/), working on RL fine-tuning for VLAs, audio understanding for robots, and world models.

<h2 class="news-heading" style="margin-top: 2.2rem;">News</h2>

{% assign news_items = site.news | sort: "date" | reverse %}
<div class="news-list">
{% for item in news_items limit: 3 %}
<div class="news-row">
<div class="news-date">{{ item.date | date: "%b %-d, %Y" }}</div>
<div class="news-body">{{ item.content }}</div>
</div>
{% endfor %}
</div>
{% if news_items.size > 3 %}
<details class="news-expander" style="margin-top: 0.6rem;">
<summary>Show more news</summary>
<div class="news-list" style="margin-top: 1rem;">
{% for item in news_items offset: 3 %}
<div class="news-row">
<div class="news-date">{{ item.date | date: "%b %-d, %Y" }}</div>
<div class="news-body">{{ item.content }}</div>
</div>
{% endfor %}
</div>
</details>
{% endif %}
