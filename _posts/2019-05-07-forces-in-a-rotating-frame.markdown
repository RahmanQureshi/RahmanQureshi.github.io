---
layout: post
title:  "Forces in a Rotating Frame"
date:   2019-05-07 21:00:00 -0400
categories: robotics
---

# Motivation

There are some OK intuitive explanations for what the coriolis, centrifugal, and euler forces are and how they work so I will not repeat that here. However, I felt that the derivations online were lacking. The system being analyzed was unclear due to a lack of a diagram. Unfair, clever tricks were used (e.g. but you must also take a derivative with respect to the basis vectors as well because they also change with time)! Too much detail was put into breaking down how to take a derivative and the big picture was missed.

I like derivations that are more like 'explorations.' We define a system, start from simple observations, 'explore' and come to results. To that end, I will derive the forces acting in a rotating reference frame from a simple and intuitive vector equation: $$r^{p0} = r^{10} + r^{p1}$$.


# Notation

TODO.

$$
\omega_{10} = angular velocity of frame 1 with respect to frame 0.
$$

# System

![Image is unavailable. Sorry for the inconvenience.](/assets/point_in_rotating_frame.svg)


# Coriolis Force, Centrifugal Force, Euler Force

The vector from frame 0 to p equals the vector from frame 0 to 1 plus the vector from frame 1 to p. This is easy to reason and can be geometrically seen in the figure above. At this point, I want to emphasize that we are making no assumptions about the motion of frame 0 or frame 1 or p. 

$$
r^{p0} = r^{10} + r^{p1}
$$

We can rewrite the equation in terms of specific basis, specifically in terms of frame 0. Notice that we are rotating the vector $$r^{p1}$$ from frame 1 into frame 0. The motivation for this is because $$r_1^{p1}$$ is what an observer in frame 1 sees. the motivation for putting everything in terms of frame 0 is because eventually we know we will define an inertial frame where Newton's law will hold and arbitrarily we will select frame 0.

$$
r_0^{p0} = r_0^{10} + T_{01} r_1^{p1}
$$

Next, we take the derivative twice. This is just calculus.

$$
\dot{r}_0^{p0} = \dot{r}_0^{10} + T_{01} \dot{r}_1^{p1} + \omega_{10} \times T_{01} r_1^{p1} \\

\ddot{r}_0^{p0} = \ddot{r}_0^{10} + 
                  T_{01} \ddot{r}_1^{p1} + \omega_{10} \times T_{01} \dot{r}_1^{p1} + 
                  \omega_{10} \times (T_{01} \dot{r}_1^{p1} + \omega_{10} \times T_{01} r_1^{p1}) + \frac{d\omega_{10}}{dt} \times T_{01} r_1^{p1} \\

\ddot{r}_0^{p0} = \ddot{r}_0^{10} + T_{01} \ddot{r}_1^{p1} +
                  2 ( \omega_{10} \times T_{01} \dot{r}_1^{p1} ) + 
                  \omega_{10} \times \omega_{10} \times T_{01} r_1^{p1} + 
                  \frac{d\omega_{10}}{dt} \times T_{01} r_1^{p1} \\

$$

The last step was only expansion. Already the familiar forms of the coriolis, centrifugal and euler forces are appearing. A few comments about this equation. First, there was absolutely no assumption made about the motion of the frames or the points. This is a very general equation. Second, the equation is saying that the acceleration of point p wrt frame 0 is given by adding the acceleration of frame 1 wrt 0, $$\ddot{r}_0^{10}$$, plus the acceleration of the point p wrt frame 1, $$T_{01} \ddot{r}_1^{p1}$$ plus other terms due to the relative rotation.