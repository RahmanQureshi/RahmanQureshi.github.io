---
short_name: undel
layout: project
title: Bond Strength Detection Using ML
description: >-
    
date: 2015-08-02 00:00:00 -0500
---

I spent a summer working in the Ultrasonic Nondestructive Evaluation Laboratory at UofT. An industry sponsored project, the goal was to develop a method of detecting bond strength between an adhesive and primer using ultrasound. My supervisor and I developed an SVM that could classify bond strength as weak or strong with high accuracy on one specific type of pipe.

An example cross-section of the pipe used in this research:
<img src="/assets/projects/{{page.short_name}}/project-ndt-1.jpg" />

An ultrasonic pulse is emitted at the pipe and the echoes are recorded.
<img src="/assets/projects/{{page.short_name}}/project-ndt-2.jpg" />
<img src="/assets/projects/{{page.short_name}}/project-ndt-10.jpg" />

Peak detection was used to generate important features. We used FFT to eliminate high frequency noise.
<img src="/assets/projects/{{page.short_name}}/project-ndt-4.jpg" />
<img src="/assets/projects/{{page.short_name}}/project-ndt-5.jpg" />

A signal attenuation constant was part of our physical model for the adhesive. It had to be computed within a statistical confidence.
<img src="/assets/projects/{{page.short_name}}/project-ndt-8.jpg" />

A decay constant for the primer echoes was fit to the signals obtained from samples of weak and strong bonds. A clear correlation is observed.
<img src="/assets/projects/{{page.short_name}}/project-ndt-9.jpg" />