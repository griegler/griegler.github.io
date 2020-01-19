---
layout: none
title:  "ATGV-Net: Accurate Depth Super-Resolution"
teaser: "/images/teaser/dsr.png"
authors: "Gernot Riegler, Matthias Rüther, Horst Bischof"
conference: ECCV
year: 2016 (poster)
comments: false
---

In this work we present a novel approach for single depth map super-resolution.
Modern consumer depth sensors, especially Time-of-Flight sensors, produce dense depth measurements, but are affected by noise and have a low lateral resolution.
We propose a method that combines the benefits of recent advances in machine learning based single image super-resolution, i.e. deep convolutional networks, with a variational method to recover accurate high-resolution depth maps.
In particular, we integrate a variational method that models the piecewise affine structures apparent in depth data via an anisotropic total generalized variation regularization term on top of a deep network.
We call our method ATGV-Net and train it end-to-end by unrolling the optimization procedure of the variational method.
To train deep networks, a large corpus of training data with accurate ground-truth is required.
We demonstrate that it is feasible to train our method solely on synthetic data that we generate in large quantities for this task.
Our evaluations show that we achieve state-of-the-art results on three different benchmarks, as well as on a challenging Time-of-Flight dataset, all without utilizing an additional intensity image as guidance.

[Paper](/papers/dsr.pdf)
[Supplemental Material](http://rvlab.icg.tugraz.at/documents/riegler/eccv16_supp.pdf)
[Code and Data](https://github.com/griegler/primal-dual-networks)
