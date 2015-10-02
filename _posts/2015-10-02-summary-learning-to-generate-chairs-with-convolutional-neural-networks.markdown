---
layout: post
title:  "Summary: Learning to Generate Chairs with Convolutional Neural Networks"
comments: true
date:   2015-10-02 15:00:00
categories: summary paper deep-learning generative
---

[Link to the paper](http://arxiv.org/abs/1411.5928), CVPR'15

# Summary
The paper presents a generative ConvNet to generate images of different chairs.
The input to the network is the class of the chair (one-hot encoding), a view vector (sine and cosine of azimuth and elevation of the camera), and a transformation vector (translation, in-plane rotation, zoom, changing hue, saturation and brightness).
The input gets first encoded in a full-connected network and the last fully-connected layer gets reshaped to a feature map.
To generate a high-resolution output a sequence of **unpooling and convolutions layers** are subsequently evaluated.
The unpooling operation is just an \\(2 \times 2\\) upscaling operation, where interpolated values are set to zero.
Interestingly, the network hast two such output streams.
One for the actual output image, and another one for a segmentation mask.
However, the segmentation mask is only used for visualization.
The network architecture is depicted below.

![Network architecture]({{ site.url }}/assets/learning_to_generate_chairs_with_convolutional_neural_networks.png)
*Architecture of the generative network. Image taken from Dosovitskiy et al. 'Learning to Generate Chairs with Convolutional Neural Networks', CVPR, 2015, p.3*

For both outputs a MSE loss is used for training. 
However, the for the RGB output the background is masked out by the ground-truth segmentation mask.
This helps to avoid learning the background instead of the objected of interest.
The authors **train first a smaller network** (dropping the last layer) to initialize the weights of the full model.

The paper presents an exhaustive evaluation of the network, like the influence of different neurons in the fully connected network (*e.g.* they found a neuron that is responsible for zooming).
Further, the network can interpolate between viewpoints and different chair classes.


# Thoughts
It is a nice idea to invert the ConvNet to generate images.
In contrast to adversarial networks ([Goodfellow et al.][1], [Denton et al.][2]) it is able to generate an **output of higher resolution**, but for a more constraint setting.
Further, I wonder if the segmentation can be incorporated directly into a single output, *e.g.* using a Hadamard product, and could we use the ConvNet the other way around as a feature representation?
Finally, I would like to see this method employed on other datasets, like faces and pose estimation.

[1]: http://arxiv.org/abs/1406.2661
[2]: http://arxiv.org/abs/1506.05751
