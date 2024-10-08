---
layout: archive
title: # "Resume"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* M.S. in Computer Science, Texas A&M University, Dec 2024 (expected)
* B.S. in Computer Science, Oregon State University, 2023

Projects
======
  <ul>{% for post in site.portfolio reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Work experience
======
* Jun 2024-Present: Research Assistant
  * Texas A&M University
  * Duties includes: 
    - Responsible for designing and implementing deep learning algorithms using the PyTorch framework for lossy compression of Channel State Information (CSI) to optimize data transmission efficiency in communication systems.
    - Conduct performance comparison experiments with existing benchmark models to assess and refine the effectiveness of the compression algorithms.
    - Perform necessary ablation studies to analyze the impact of different model components on compression performance, progressively optimizing the model structure.
    - Currently, the project is in the development and testing phase, with preliminary experiments demonstrating potential advantages in compression efficiency and data recovery quality.

* Jun 2022-Mar 2023: Teaching Assistant
  * Oregon State University
  * Duties includes: Responsible for grading, reviewing assignments. Design and implement strategies to enhance student engagement. Focus on teaching interaction and communication to achieve significant results, and have improved my personal communication abilities and teaching skills.

* Oct 2022-Jun 2023: Research Assistant
  * Oregon State University
  * Duties included: Developed a supply chain forecasting model for the automotive industry, utilizing probabilistic programming, supply chain forecasting, and data analysis techniques to optimize manufacturing processes and reduce inventory backlogs. This experience enhanced my theoretical knowledge and practical problem-solving abilities. 
  * Supervisor: Karthika Mohan
  
Skills
======
* Python, C/C++
* PyTorch, Docker, Git, Gym, OpenCV
* Machine Learning, Reinforcement Learning, Computer Vision


Download my CV [here](https://jaron-u.github.io/files/JianglongYu_Resume.pdf)