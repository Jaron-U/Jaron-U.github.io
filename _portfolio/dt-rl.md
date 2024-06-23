---
title: "Decision Transformer for Atari Games"
excerpt: "Play Atari games using Decision transformer Reinforcement Learning<br/><img src='/images/dtrl.png'>"
collection: portfolio
---

Project Link: [https://github.com/Jaron-U/decision-transformer-atari](https://github.com/Jaron-U/decision-transformer-atari)

This study applies Decision Transformers (DT), which reimagine reinforcement
learning (RL) as sequence modeling using Transformer architecture, to the Atari
game Pong. Traditional RL methods, often hindered by complexities and sparse
rewards, are outperformed by DTs that utilize complete trajectories of states,
actions, and rewards for enhanced learning. We have advanced the DT framework
by integrating a loss-decay algorithm and conducting an ablation study on context
length, which significantly improves performance over conventional offline RL
algorithms. Furthermore, we explored the effects of model pruning on DT, aiming
to optimize efficiency without compromising performance. These adaptations
not only enhance strategic gameplay in Pong but also underscore the broader
applicability of DTs in addressing complex AI challenges.

This is the ppt of the project: 
If the embedded PDF below does not load, you can <u><a href="https://jaron-u.github.io/files/ECEN743_Presentation.pdf">download it here.</a></u> <br/> <embed src="https://jaron-u.github.io/files/ECEN743_Presentation.pdf" type="application/pdf" width="100%" />