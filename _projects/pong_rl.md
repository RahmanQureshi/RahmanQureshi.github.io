---
short_name: pong_rl
layout: project
title: Pong AI — Deep Q Reinforcement Learning
description: >-
    
date: 2020-02-02 00:00:00 -0500
---

[Source code](https://github.com/RahmanQureshi/pong-rl)

In this project, I replicated an influential reinforcement learning paper published in 2015: [Human-level control through deep reinforcement learning](https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf). I self-studied [CSC421 Deep Learning](http://www.cs.toronto.edu/~rgrosse/courses/csc421_2019/) which had a publically available syllabus and whose lectures were based on accessible research papers, and after completing all the [homework](https://github.com/RahmanQureshi/csc421), I wanted to do a "capstone."

The final results are shown below (the neural network is the green player). The most interesting thing, in my opinion, is how the neural net learned to deflect the ball in such a manner that the deterministic bot could not hit it back. This is in contrast to the random AI which, even when it hits the ball back, the deterministic bot is able to respond.

| Randomly Sampled Actions  | Trained Deep Q Neural Network |
| ------------- | ------------- |
| <img src="/assets/projects/{{page.short_name}}/pong_random.gif" style="width:200px; border: 1px solid black;" /> | <img src="/assets/projects/{{page.short_name}}/pong_success.gif" style="width:200px; border: 1px solid black;" /> |
