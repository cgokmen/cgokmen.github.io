---
layout: page
title: About Me
author: Cem Gokmen
# cover: true
---

Hi! I'm Cem (pronounced Jem - Turkish phonetics!), I'm currently a **CS PhD Candidate at Stanford, specializing in Embodied AI and Robotics** at Stanford University at the
[Stanford Vision & Learning Lab](http://svl.stanford.edu/) advised by Prof. Fei-Fei Li.

I develop machine learning algorithms enabling robots to perform complex, long-horizon tasks in real-world environments using techniques like learning from demonstrations, reinforcement learning, sim-to-real transfer, and leveraging off-the-shelf LLM/VLM models. I also have extensive experience building simulation environments and benchmarks to support this research.

---

## Highlighted Publications

### BEHAVIOR-1K: A Benchmark for Embodied AI

_Co-First Author, CoRL 2022 Oral, Best Paper Nominee_

BEHAVIOR-1K is a human-centered embodied AI benchmark featuring 1,000 diverse, everyday activities. This ongoing, four-year project addresses challenges like long-horizon tasks and complex manipulations in realistic environments. It provides a robotics research direction grounded in human needs, offering unprecedented diversity and realism compared to traditional benchmarks.

The project includes a 6k-object, 50-scene dataset with 1,000 task definitions and 4,000 nouns in the BEHAVIOR-1K knowledgebase. It also features OmniGibson and iGibson, high-fidelity simulation environments built on Omniverse Isaac Sim and PyBullet, respectively.

Website: [https://behavior.stanford.edu](https://behavior.stanford.edu)\
Paper: [https://arxiv.org/abs/2403.09227](https://arxiv.org/abs/2403.09227)\
Knowledgebase: [https://behavior.stanford.edu/knowledgebase/](https://behavior.stanford.edu/knowledgebase/)  \
OmniGibson: [https://github.com/StanfordVL/OmniGibson](https://github.com/StanfordVL/OmniGibson)

> <small>Li\*, Chengshu, Ruohan Zhang\*, Josiah Wong\*, Cem Gokmen\*, Sanjana
> Srivastava\*, Roberto Martin-Martin\*, Chen Wang\*, et al. 2022.
> “BEHAVIOR-1K: A Benchmark for Embodied AI with 1,000 Everyday Activities
> and Realistic Simulation.” In *6th Annual Conference on Robot Learning*.</small>

### Behavioral Cloning Value Approximation (BCVA)

_First Author_

BCVA is a method to predict failures in robot policies trained using Imitation Learning where no state value estimate is available by default. This innovation enables robots to autonomously ask for help when needed. In real-world trials at Everyday Robots, BCVA demonstrated 86% precision in asking for help across over 2000 trials, particularly excelling in complex tasks like latched-door opening.

Paper: [https://arxiv.org/abs/2302.04334](https://arxiv.org/abs/2302.04334)

> <small>Gokmen, Cem, Daniel Ho, and Mohi Khansari. 2023. “Asking for Help:
> Failure Prediction in Behavioral Cloning Through Value Approximation.”
> In *2023 IEEE International Conference on Robotics and Automation
> (ICRA)*.</small>

### Embodied Agent Interface

_NeurIPS 2024 Benchmark Track Oral_

The Embodied Agent Interface is a framework for systematically benchmarking Large Language Models (LLMs) in embodied decision-making tasks. This project addresses the need for standardized assessment in the rapidly evolving field of LLMs in embodied environments. It enables fine-grained evaluation of LLMs' capabilities in handling complex, embodied decision-making scenarios, identifying issues like hallucinations and planning errors across 15 LLMs on benchmarks such as BEHAVIOR and VirtualHome.

Website: [https://embodied-agent-interface.github.io/](https://embodied-agent-interface.github.io/)\
Paper: [https://arxiv.org/abs/2410.07166](https://arxiv.org/abs/2410.07166)

> <small>Li, Manling, Shiyu Zhao, Qineng Wang, Kangrui Wang, Yu Zhou, Sanjana
> Srivastava, Cem Gokmen, et al. 2024. “Embodied Agent Interface:
> Benchmarking LLMs for Embodied Decision Making.” In *Neural Information
> Processing Systems Datasets and Benchmarks Track*.</small>

### BEHAVIOR Vision Suite (BVS)

_Co-First Author, CVPR 2024 Highlight_

BVS is a toolset designed to generate fully customizable synthetic data for evaluating computer vision models. It addresses limitations in real-world datasets such as poor labeling and lack of diversity. BVS facilitates controlled experiments by allowing adjustments at multiple levels, including scene, object, and camera parameters. This capability supports various tasks including model robustness testing, scene understanding, and simulation-to-real transfer for vision tasks like unary and binary state prediction.

Website: [https://behavior-vision-suite.github.io/](https://behavior-vision-suite.github.io/)\
Paper: [https://arxiv.org/abs/2405.09546](https://arxiv.org/abs/2405.09546)

> <small>Ge\*, Yunhao, Yihe Tang\*, Jiashu Xu\*, Cem Gokmen\*, Chengshu Li, Wensi
> Ai, Benjamin Jose Martinez, et al. 2024. “BEHAVIOR Vision Suite:
> Customizable Dataset Generation via Simulation.” In *Proceedings of the
> IEEE/CVF Conference on Computer Vision and Pattern Recognition </small>

### ACDC: Automated Creation of Digital Cousins

ACDC (Automated Creation of Digital Cousins) is a novel approach to bridge the gap between simulation and real-world robotics training. It introduces the concept of "digital cousins" – virtual assets or scenes that exhibit similar geometric and semantic affordances to real-world counterparts without explicitly modeling them. This approach reduces the cost of generating analogous virtual environments while facilitating better cross-domain generalization.

Key features of ACDC include:

1. A fully automated real-to-sim-to-real pipeline for generating interactive scenes from a single RGB image.
2. A three-step process: (1) extracting per-object information from input images, (2) matching digital cousins to detected objects, and (3) generating a fully-interactive simulated scene.
3. Preservation of semantic and spatial details of input scenes, allowing accurate positioning and scaling of digital cousins.
4. Improved robustness in policy training compared to digital twins, with comparable in-domain performance and superior out-of-domain generalization.
5. Enablement of zero-shot sim-to-real policy transfer, achieving 90% success rate compared to 25% for policies trained on digital twins.

Website: [https://digital-cousins.github.io/](https://digital-cousins.github.io/)\
Paper: [https://arxiv.org/abs/2410.07408](https://arxiv.org/abs/2410.07408)

> <small>Dai, Tianyuan, Josiah Wong, Yunfan Jiang, Chen Wang, Cem Gokmen, Ruohan
> Zhang, Jiajun Wu, and Li Fei-Fei. 2024. “ACDC: Automated Creation of
> Digital Cousins for Robust Policy Learning.” In *8th Annual Conference
> on Robot Learning*.</small>

For a full list of publications, visit my [Google Scholar](https://scholar.google.com).

---

## Education

**Ph.D. in Computer Science**\
Stanford University | _Advisor: Prof. Fei-Fei Li_\
Sep. 2022 - Present

**M.Sc. in Computer Science**\
Stanford University | GPA: 4.03\
Sep. 2020 - Jun. 2022
- Google Computer Science Research Mentorship Program (CSRMP) Fellow
- Select Coursework: Deep Learning • Principles of Robot Autonomy I • Decision Making Under Uncertainty • Interactive & Embodied Learning • Convolutional Neural Networks for Visual Recognition • Machine Learning with Graphs

**B.Sc. in Computer Science with Undergraduate Research Certification**\
Georgia Institute of Technology | GPA: 3.83\
Aug. 2016 - Dec. 2018

---

## Experience

**Research Scientist Intern, NVIDIA Research**\
AI Algorithms Group, Santa Clara, CA\
Jun. 2023 - Sep. 2023
- Developed a method leveraging LLMs to generate demos for learning end-to-end transformer policies for long-horizon robotics tasks.

**AI Resident, Google X / Everyday Robots**\
Mountain View, CA\
Jun. 2022 - Sep. 2022
- Developed a method to allow robots to estimate their likelihood of success based on previous rollouts of a real-world imitation learning robot policy and decide whether to ask for help.

**Software Engineer II, Google**\
YouTube Premium Team, San Bruno, CA\
Feb. 2019 - Sep. 2020
- Implemented critical user journeys and led software design, gained expertise on in-app messaging methods, developed features across Python/C++ backends and Android/iOS/Web frontends.

---

## Teaching

**Head Course Assistant, CS 231N: Deep Learning for Computer Vision**\
Stanford University | Mar. 2024 - Jun. 2024
- Led team of 22 course assistants, planned development of assignments and exams, mentored student projects, and managed logistics for Stanford CS's most popular, 650-student course.
- See https://cs231n.stanford.edu/2024/reports.html for mentored projects.

**Course Assistant, CS 107: Computer Organization & Systems**\
Stanford University | Sep. 2020 - Aug. 2021
- Taught labs on C programming and memory for 4 semesters.
- Effectiveness rated 91% by students.

**Senior Teaching Assistant, CS 2110: Computer Organization & Programming**\
Georgia Tech College of Computing | Aug. 2017 - Dec. 2018
- Taught 3-hour weekly recitation to 75 students each semester with an effectiveness rating of 96%.
- As the Senior TA, designed and managed all course materials including homework, lab assignments, exams, and lecture activities for 400+ students.
- Planned and directed the major redesign of 6 out of 12 existing homework assignments to better highlight course objectives and harness new possibilities arising from new technologies.

---

## Skills

- **Languages**: English (Fluent), Turkish (Native), French (Advanced), Spanish (Beginner)
- **Programming**: Python, Java, C, C++, JavaScript, HTML, CSS
- **Frameworks**: PyTorch, TensorFlow, Ray, PyBullet, Omniverse, Isaac Sim, CUDA, Docker
- **Research Areas**: Reinforcement Learning, Imitation Learning, Robotics Simulation, Motion Planning, Classical Robotics
