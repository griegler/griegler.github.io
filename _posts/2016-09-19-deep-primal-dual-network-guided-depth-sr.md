---
layout: none
title:  "A Deep Primal-Dual Network for Guided Depth Super-Resolution"
teaser: "/images/teaser/gdsr.png"
authors: "Gernot Riegler, David Ferstl, Matthias Rüther, Horst Bischof"
conference: BMVC
year: 2016 (oral)
comments: false
---

In this paper we present a novel method to increase the spatial resolution of depth images.
We combine a deep fully convolutional network with a non-local variational method in a deep primal-dual network. 
The joint network computes a noise-free, high-resolution estimate from a noisy, low-resolution input depth map.
Additionally, a high-resolution intensity image is used to guide the reconstruction in the network.
By unrolling the optimization steps of a first-order primal-dual algorithm and formulating it as a network, we can train our joint method end-to-end.
This not only enables us to learn the weights of the fully convolutional network, but also to optimize all parameters of the variational method and its optimization procedure.
The training of such a deep network requires a large dataset for supervision.
Therefore, we generate high-quality depth maps and corresponding color images with a physically based renderer.
In an exhaustive evaluation we show that our method outperforms the state-of-the-art on multiple benchmarks.


[Paper](/papers/gdsr.pdf)
[Supplemental Material](http://rvlab.icg.tugraz.at/documents/riegler/bmvc16_supp.pdf)
[Code and Data](https://github.com/griegler/primal-dual-networks)
