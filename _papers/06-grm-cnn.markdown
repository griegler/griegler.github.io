---
title:  "Depth Restoration via Joint Training of a Global Regression Model and CNNs"
teaser: "/img/teaser/grm-cnn.png"
authors: "Gernot Riegler, Rene Ranftl, Matthias Rüther, Thomas Pock, Horst Bischof"
conference: BMVC
year: 2015 (poster)
comments: false
---

Denoising and upscaling of depth maps is a fundamental post-processing step for handling the output of depth sensors, since many applications that rely on depth data require accurate estimates to reach optimal accuracy. Adapting methods for denoising and upscaling to specific types of depth sensors is a cumbersome and error-prone task due to their complex noise characteristics. In this work we propose a model for denoising and upscaling of depth maps that adapts to the characteristics of a given sensor in a data-driven manner. We introduce a non-local Global Regression Model which models the inherent smoothness of depth maps. The Global Regression Model is parametrized by a Convolutional Neural Network, which is able to extract a rich set of features from the available input data. The structure of the model enables a complex parametrization, which can be jointly learned end-to-end and eliminates the need to explicitly model the signal formation process and the noise characteristics of a given sensor.Our experiments show that the proposed approach outperforms state-of-the-art methods, is efficient to compute and can be trained in a fully automatic way.

[Paper](/papers/grm-cnn.pdf)
