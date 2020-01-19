---
layout: none
title:  "Efficiently Creating 3D Training Data for Fine Hand Pose Estimation"
teaser: "/images/teaser/hand-pose-training-data.png"
authors: "Markus Oberweger, Gernot Riegler, Paul Wohlhart, Vincent Lepetit"
conference: CVPR
year: 2016 (poster)
comments: false
---

While many recent hand pose estimation methods critically rely on a training set of labelled frames, the creation of such a dataset is a challenging task that has been overlooked so far. As a result, existing datasets are limited to a few sequences and individuals, with limited accuracy, and this prevents these methods from delivering their full potential. We propose a semi-automated method for efficiently and accurately labeling each frame of a hand depth video with the corresponding 3D locations of the joints: The user is asked to provide only an estimate of the 2D reprojections of the visible joints in some reference frames, which are automatically selected to minimize the labeling work by efficiently optimizing a sub-modular loss function. We then exploit spatial, temporal, and appearance constraints to retrieve the full 3D poses of the hand over the complete sequence. We show that this data can be used to train a recent state-of-the-art hand pose estimation method, leading to increased accuracy.

[Paper](/papers/hand-pose-training-data.pdf)
