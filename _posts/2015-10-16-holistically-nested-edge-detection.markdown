---
layout: post
title:  "Summary: Holistically-Nested Edge Detection"
comments: true
date:   2015-10-16 15:00:00
category: summary
---

[Link to the paper](http://arxiv.org/abs/1504.06375), ICCV'15.


# Summary
The paper presents a ConvNet approach for edge detection that approaches human performance on the BSDS500 benchmark.
First, the paper gives a nice overview of different network architectures that incorporates different image scales.
The authors themselves utilize a, what the name, holistically-nested network.

![Network architecture]({{ site.url }}/assets/holistically_nested_edge_detection.png)
*Overview of different multi-scale network architecture. Image taken from Xie and Tu 'Holistically-Nested Edge Detection', ICCV, 2015, p.3*

Each stage outputs the edge map on a different scale. 
These **side outputs** are already **super-vised** (*c.f.* Deeply-Supervised Nets by Lee et al.) and fused to a single output via a weighted convolution (that is initialized to average the outpus, \\(1/5\\)).
The loss for the side output is a **cross-entropy loss** that is **weighted by the fraction of edge pixels** in the edge pixels, because the classes edge and background are highly unbalanced. 
For the fusion the side-outputs get **upsampled by a deconvolution**, whereas the weights of the deconvolution are fixed to perform a linear interpolation of the data.
They utilize a pre-trained VGGNet16 model and train their model on the BSDS500 and NYU2 dataset (with HHA encoding).
In the appendix the show that with more data-augmentation (additionally rescaling to rotating and flipping) the effect of deep supervision diminishes. 


# Thoughts
An interesting paper that contains some nice tricks and the overview of different multi-scale architectures is really nice.
What I think is not so intuitive, is why simple averaging of the average side-outputs and the fusion-output gives overall better results
