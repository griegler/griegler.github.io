---
layout: post
title:  "Summary: Predicting Depth, Surface Normals and Semantic Labels with a Common Multi-Scale Convolutional Architecture"
comments: true
date:   2015-09-30 15:00:00
categories: summary paper deep-learning depth-estimation
---

[Link to the paper](http://arxiv.org/abs/1411.4734), ICCV'15

# Summary
The paper by David Eigen and Rob Furgus can be seen as an extension to their [previous paper]({% post_url 2015-09-30-summary-depth-map-prediction-from-a-single-image-using-a-multi-scale-deep-network %}).
The multi-scale architecture of the network is advanced by another scale (so instead of two scale-stages, they use three in this paper).
A subtle difference is that not the predicted depth map of the coarse map is integrated into the feature maps of the upper scale network, but the complete feature maps of the lower scale network.
This three-scale architecture is then used for three different tasks: (1) depth prediction from a single RGB image, (2) surface normal prediction, and (3) semantic segmentation from RGB-D input.

For the first task, the loss from their previous paper is extended by penalizing also the first-order derivative of the predicted depth map:

$$ L(y, t) = \frac{1}{n} \sum_{i} d_i^2 - \frac{1}{2n^2} (\sum_{i} d_i)^2 + \frac{1}{n} \sum_i (\nabla_x d_i)^2 + (\nabla_y d_i)^2 .$$

For the surface normal estimation task, they utilize the negative dot product as error metric and for semantic segmentation a pixel-wise cross-entropy loss.



# Thoughts
The author noticed in Section 5.3 that the networks can be combined (for depth and normals), by using common coarse network, but it does not improve performance.
Therefore, I wonder if the network does really learn different representations in the first layers for the different tasks?
Or can you train just a single network for all three tasks, *e.g.* state it as multi-task learning problem.
Should this not make the feature representation more robust?
An interesting evaluation for the depth estimation would be a comparison between the new loss and the one from their previous paper, just to see if the performance increase is contributed to the larger network or the new loss. 
