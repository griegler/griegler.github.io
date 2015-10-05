---
layout: post
title:  "Summary: Learning Depth from Single Monocular Images Using Deep Convolutional Neural Fields"
comments: true
date:   2015-10-05 17:00:00
categories: summary paper deep-learning depth CRF
---

[Link to the paper](http://arxiv.org/abs/1502.07411), arXiv.
Extended version of their CVPR'15 [paper](http://arxiv.org/abs/1411.6387)


# Summary
The paper presents an approach for depth estimation from a single RGB image, *c.f.* this [post]({% post_url 2015-09-30-summary-depth-map-prediction-from-a-single-image-using-a-multi-scale-deep-network %}) and this [post]({% post_url 2015-10-01-summary-predicting-depth-surface-normals-and-semantic-labels-with-a-common-multi-scale-convolutional-architecture %}), based on a ConvNet and a Conditioned Random Field (CRF).
The CRF is integrated into the Network via a **specific loss function** that incorporates unary and pair-wise potentials.
The unary network is a vanilla ConvNet (pretrained on ImageNet data), whereas the "network" for the pair-wise potentials is in fact a linear regression based on similarity measures between super-pixels.
Due to the special design of the potentials (**quadratic form**) it can be solved in closed form.
Therefore, the inference and the back-propagation of the gradients is feasible.

The networks are **evaluated on super-pixels** (SLIC) of the image.
This has the effect that many convolutional operations for the unary network are redundant.
To overcome this limitations, the authors introduce a **super-pixel pooling** scheme.
The convert the unary network to a fully-convolutional one and map the super-pixel locations in the last feature map (with \\(d\\) channels).
These feature vectors of length \\(d\\) are averaged.
This improves the inference speed of the network by a factor of approx. 10.

The evaluations show the benefit of the CRF with pair-wise potentials over the unary output alone.
Further, the quantitative results show slightly better results than current state-of-the-art approaches (*e.g.* [Eigen et al.]({% post_url 2015-09-30-summary-depth-map-prediction-from-a-single-image-using-a-multi-scale-deep-network %})).
The qualitative results, however, look much sharper than the results of Eigen et al..


# Thoughts
I like the combination of a continuous CRF and ConvNets, although it is very similar to [[28]](http://www.cl.cam.ac.uk/~pr10/publications/eccv14.pdf).
Further, I do not understand why the authors state at several points in the paper that the architecture can also be trained with deeper networks for the pair-wise potentials, but never demonstrate it. 
The current approach relies still on hand-crafted features.
