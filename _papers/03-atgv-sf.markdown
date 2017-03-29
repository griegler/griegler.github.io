---
title:  "aTGV-SF: Dense Variational Scene Flow through Projective Warping and Higher Order Regularization"
teaser: "/img/teaser/atgv-sf.png"
authors: "David Ferstl, Christian Reinbacher, Gernot Riegler, Matthias Ruether, Horst Bischof"
conference: 3DV
year: 2014 (oral)
comments: false
---

In this paper we present a novel method to accurately estimate the dense 3D motion field, known as scene flow, from depth and intensity acquisitions. The method is formulated as a convex energy optimization, where the motion warping of each scene point is estimated through a projection and back-projection directly in 3D space. We utilize higher order regularization which is weighted and directed according to the input data by an anisotropic diffusion tensor. Our formulation enables the calculation of a dense flow field which does not penalize smooth and non-rigid movements while aligning motion boundaries with strong depth boundaries. An efficient parallelization of the numerical algorithm leads to runtimes in the order of 1s and therefore enables the method to be used in a variety of applications. We show that this novel scene flow calculation outperforms existing approaches in terms of speed and accuracy. Furthermore, we demonstrate applications such as camera pose estimation and depth image superresolution, which are enabled by the high accuracy of the proposed method. We show these applications using modern depth sensors such as Microsoft Kinect or the PMD Nano Time-of-Flight sensor.

[Paper](/papers/atgv-sf.pdf)
