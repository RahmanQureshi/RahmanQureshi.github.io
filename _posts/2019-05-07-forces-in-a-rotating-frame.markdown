---
layout: post
title:  "Forces in a Rotating Frame"
date:   2019-05-07 21:00:00 -0400
categories: robotics
---

This post derives newton's law in a rotating frame of reference using the more generalized framework of coordinate frames and rotation matrices. It has a nice intermediate result which is a general formula for computing the acceleration of a point in a new reference frame. It also has the benefit of starting from a simple and intuitive vector equation: $$r^{p0} = r^{10} + r^{p1}$$.

# Notation

- $$\omega_a^{cb}$$ : angular velocity of c with respect to b represented in the coordinates of frame a.
- $$r_a^{cb}$$: vector from b to c represented in the coordinates of frame a.
- $$T_{ba}$$: matrix that rotates vectors from frame a into frame b

# System Setup

This section explains the geometric picture. Define two frames, frame 0 and frame 1, and say frame 0 is an inertial frame and frame 1 is rotating about some vector $$\omega$$. Next, we define a point p. An observer in frame 1 is watching point p: $$r_1^{p1}(t)$$. He wants to apply newton's law to understand it's motion. He knows that the frame he is in is not inertial, so he cannot just apply $$F=ma$$.

| <img src="/assets/point_in_rotating_frame.svg" alt="Image is unavailable. Sorry." style="margin-left: auto; margin-right: auto; width: 100%; display: block;"/> |
| <center> Figure: Frame 0 is an inertial frame and frame 1 is rotating w.r.t frame 1. An observer in frame 1 is watching point p.</center> |

# Forces in a Rotating Frame: Coriolis Force, Centrifugal Force, Euler Force

The vector from frame 0 to p equals the vector from frame 0 to 1 plus the vector from frame 1 to p. This is easy to reason and can be geometrically seen in the figure above. At this point, I want to emphasize that there are no assumptions about the motion of frame 0 or frame 1 or p. 

$$
r^{p0} = r^{10} + r^{p1}
$$

We can rewrite the equation in terms of specific basis, specifically in terms of frame 0 since we are after the point's acceleration in an inertial frame. Notice that we are rotating the vector $$r^{p1}$$ from frame 1 into frame 0. The motivation for this is because $$r_1^{p1}$$ is what an observer in frame 1 sees.

$$
r_0^{p0} = r_0^{10} + T_{01} r_1^{p1}
$$

Next, we take the derivative twice to find the acceleration of point p w.r.t frame 0. This is just calculus.

$$
\dot{r}_0^{p0} = \dot{r}_0^{10} + T_{01} \dot{r}_1^{p1} + \omega_0^{10} \times T_{01} r_1^{p1} \\

\ddot{r}_0^{p0} = \ddot{r}_0^{10} + 
                  T_{01} \ddot{r}_1^{p1} + \omega_0^{10} \times T_{01} \dot{r}_1^{p1} + 
                  \omega_0^{10} \times (T_{01} \dot{r}_1^{p1} + \omega_0^{10} \times T_{01} r_1^{p1}) + \frac{d\omega_0^{10}}{dt} \times T_{01} r_1^{p1} \\

\ddot{r}_0^{p0} = \ddot{r}_0^{10} + T_{01} \ddot{r}_1^{p1} +
                  2 ( \omega_0^{10} \times T_{01} \dot{r}_1^{p1} ) + 
                  \omega_0^{10} \times (\omega_0^{10} \times T_{01} r_1^{p1}) + 
                  \frac{d\omega_0^{10}}{dt} \times T_{01} r_1^{p1} \\

\ddot{r}_0^{p0} = \ddot{r}_0^{10} + \ddot{r}_0^{p1} +
                  2 ( \omega_0^{10} \times \dot{r}_0^{p1} ) + 
                  \omega_0^{10} \times (\omega_0^{10} \times r_0^{p1}) + 
                  \frac{d\omega_0^{10}}{dt} \times r_0^{p1} \\

$$

The last two steps were only expansion and then applying the rotation matrices. Already the familiar forms of the coriolis, centrifugal and euler forces are appearing. A few comments about this equation. First, there was absolutely no assumption made about the motion of the frames or the points. This is a very general equation. Second, the equation is saying that the acceleration of point p w.r.t. frame 0 is given by adding the acceleration of frame 1 w.r.t 0 ($$\ddot{r}_0^{10}$$) plus the acceleration of the point p w.r.t. frame 1 ($$\ddot{r}_0^{p1}$$) plus other terms due to the relative rotation.

Now we introduce two assumptions. First, we assume that frame 0 is an inertial reference frame. This means that we can use Newton's law. Second, we assume that frame 1 is only rotating with respect to frame 0, and it is not moving/accelerating (e.g. $$\ddot{r}_0^{10} = 0$$).

$$
F_0 = m \ddot{r}_0^{p0} \\
F_0 = m \ddot{r}_0^{p1} +
      2 m ( \omega_0^{10} \times \dot{r}_0^{p1} ) + 
       m \omega_0^{10} \times (\omega_0^{10} \times r_0^{p1}) + 
       m \frac{d\omega_0^{10}}{dt} \times r_0^{p1} \
$$

This equation is true no matter what basis we work in, so we change it to frame 1 because that is the frame the observer is in and he will view and represent the coordinates of p and his own frame's rotation in the basis of that frame. Mathematically though, you can multiply both sides by $$T_{10}$$ and use the following fact: if $$a$$ and $$b$$ are vectors and $$M$$ is an invertible matrix, then $$(Ma) \times (Mb) = (detM)M^{-T}(a \times b)$$.
> hint: remember that any rotation matrix $$T_{ab} \in SO(3)$$, where $$SO(3)$$ is the special orthogonal group. Look up the properties of this set!

$$
F_1 = m \ddot{r}_1^{p1} +
      2 m ( \omega_1^{10} \times \dot{r}_1^{p1} ) + 
       m \omega_1^{10} \times (\omega_1^{10} \times r_1^{p1}) + 
       m \frac{d\omega_1^{10}}{dt} \times r_1^{p1} \
$$

The last thing to notice is that $$ m \ddot{r}_1^{p1} $$ is mass times the acceleration of point p w.r.t. frame 1. This is what we are after. We want to find a set of forces so Newton's law holds in frame 1 and we can treat it as an inertial frame. Rearranging for $$ m \ddot{r}_1^{p1} $$:

$$
\bbox[2pt,border:1px solid red]{
m \ddot{r}_1^{p1} = F_1
      - 2 m ( \omega_1^{10} \times \dot{r}_1^{p1} )
      - m \omega_1^{10} \times (\omega_1^{10} \times r_1^{p1}) 
      - m \frac{d\omega_1^{10}}{dt} \times r_1^{p1} \
}
$$

This is the final, desired result. Recall the [definitions of the coriolis, centrifugal and euler forces](https://en.wikipedia.org/wiki/Coriolis_force):
- Corilois Force: $$ - 2 m ( \omega_1^{10} \times \dot{r}_1^{p1} ) $$
- Centrifugal Force: $$ - m \omega_1^{10} \times (\omega_1^{10} \times r_1^{p1}) $$
- Euler Force: $$ - m \frac{d\omega_1^{10}}{dt} \times r_1^{p1} $$

This equation tells us that in a rotating frame, mass times acceleration is equal to the applied force plus the three fictitious forces defined above.
