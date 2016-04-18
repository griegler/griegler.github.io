---
layout: post
title:  "Summary: Accurate Image Super-Resolution Using Very Deep Convolutional Networks"
comments: true
date:   2015-11-20 14:00:00
category: summary
---

[Link to the paper](http://arxiv.org/abs/1511.04587).


# Summary
This paper by J. Kim et al. demonstrates how to train a very deep ConvNet for Single Image Super-Resolution (SISR).
The key ingredients are **learning the residual** (high-resolution target minus low resolution input) for faster convergence and **increasing the learning rate**.
To avoid exploding gradients the gradients are clamped in the range of \\(\left(-\frac{\theta}{\eta}, \frac{\theta}{\eta}\right)\\), where \\(\eta\\) is the actual learning rate.
For their experiments they use a 10 and 20 layer network of \\(64 \times 3 \times 3\\) filters.
The initial learning rate was set to 0.1 and was decreased by a factor of 10 every 20 epochs (80 epochs in total).


# Thoughts
The performance increase on the various benchmarks (Set5, Set9, B100 and Urban100) is remarkable.
It seems that the larger context of the network really improves the results.
For the test-setting I was missing the \\(\theta\\) parameter for the gradient clipping.

