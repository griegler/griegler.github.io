---
title:  "OctNet: Learning Deep 3D Representations at High Resolution"
teaser: "/img/teaser/octnet.png"
authors: "Gernot Riegler, Ali Osman Ulusoy, Andreas Geiger"
conference: CVPR
year: 2017 (oral)
comments: false
---

We present OctNet, a representation for deep learning with sparse 3D data. 
In contrast to existing models, our representation enables 3D convolutional networks which are both deep and high resolution. 
Towards this goal, we exploit the sparsity in the input data to hierarchically partition the space using a set of unbalanced octrees where each leaf node stores a pooled feature representation.
This allows to focus memory allocation and computation to the relevant dense regions and enables deeper networks without compromising resolution. 
We demonstrate the utility of our OctNet representation by analyzing the impact of resolution on several 3D tasks including 3D object classification, orientation estimation and point cloud labeling.


[Paper](https://arxiv.org/abs/1611.05009)
[Code](https://github.com/griegler/octnet)
