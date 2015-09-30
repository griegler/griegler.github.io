---
layout: post
title:  "Summary: Maximum-Margin Structured Learning with Deep Networks for 3D Human Pose Estimation"
comments: true
date:   2015-09-29 10:00:00
categories: summary paper deep-learning pose-estimation
---

[Link to the paper](http://arxiv.org/abs/1508.06708), accepted to ICCV'15

# Summary
The paper presents a ConvNet that transforms an image and a pose vector to a common sate vector (**embedding**). 
The **similarity** between these embeddings is measured via a simple **dot product**. 
For training of the network a **maximum margin cost** is utilized, similar to the loss in structured SVMs.
Further, to aid training of the feature representation (image to pose embedding), a simple L2 loss is used on the pose vector (regression task).
Therefore, it falls into the category of multi-task learning.
An important detail is the training procedure that has to alternate between finding the most-violating pose and running back-propagation.
For testing, the input is a test image and a pose vector. 
To find the most suitable pose, it has iterate over all poses from the training set and use the one that maximizes the score of the dot product (or take the average over N samples, or use a annealing particle filter).

# Thoughts
A quantitative evaluation on other datasets would be nice.
This would ease the comparison to other works in this field.

Another point concerns the inference.
Would it be possible to start from a pose vector for initialization and then use a gradient descent scheme for the pose vector to find the most suitable one.
This idea is related to the work of [Mahendran and Vedaldi][1]


[1]: http://www.robots.ox.ac.uk/~vedaldi/assets/pubs/mahendran15understanding.pdf
