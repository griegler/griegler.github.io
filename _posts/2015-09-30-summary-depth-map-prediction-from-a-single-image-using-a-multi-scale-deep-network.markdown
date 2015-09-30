---
layout: post
title:  "Summary: Depth Map Prediction from a Single Image using a Multi-Scale Deep Network"
comments: true
date:   2015-09-30 15:00:00
categories: summary paper deep-learning depth-estimation
---

[Link to the paper](http://arxiv.org/abs/1406.2283), NIPS'14

# Summary
The paper presents an approach for estimating a depth map from a single intensity image based on a ConvNet.
As one can imagine, this is a highly ambiguous task.
The authors, David Eigen, Christian Puhrsch and Rob Fergus, state this problem as a machine learning task. 
First, they train a **coarse** network that predicts a rough estimate of the depth map given the intensity image as input.
The weights of this network are pre-trained on the ImageNet classification task.
Further, the estimated depth map is the output after two fully-connected layers (but the size is a fourth of the input size).
It has therefore information of the whole image.
In contrast, the **fine-scale** network consists only of three convolutional layers.
The output of the coarse network get concatenated to the feature maps of the first convolutional layer.

Given the observation that a lot of the error can be contributed to the global scale estimation, the authors propose a new error metric.
With \\(d_i = \log y_i - \log t_i\\), the metric is defined as

$$ L(y, t) = \frac{1}{n^2} \sum_{i,j} ((\log y_i - \log y_j) - (\log t_i - \log t_j) )^2 $$

$$ L(y, t) = \frac{1}{n} \sum_{i} d_i^2 - \frac{1}{n^2} (\sum_{i} d_i)^2 $$

This metric measures the relative distances instead the absolute one.
For training the influence is further adjusted with a parameter \\(\lambda\\):

$$ L(y, t) = \frac{1}{n} \sum_{i} d_i^2 - \frac{\lambda}{n^2} (\sum_{i} d_i)^2 $$

The evaluation is performed on the NYU Depth v2 and KITTI benchmarks. 
To extend the training set, data augmentation is performed (scaling, rotation, translation, color, flips).


# Thoughts
The local fine-scale network seems to improve the quantitative results only marginally (Tab. 1 and 2).
However, the qualitative results get really better.
The authors state that the networks are trained one after the other.
Why is no joint training performed?
Would this improve, or decrease the performance?
