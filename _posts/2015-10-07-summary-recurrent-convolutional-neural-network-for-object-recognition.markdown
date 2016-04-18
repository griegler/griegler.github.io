---
layout: post
title:  "Summary: Recurrent Convolutional Neural Network for Object Recognition"
comments: true
date:   2015-10-07 17:00:00
category: summary
---

[Link to the paper](http://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Liang_Recurrent_Convolutional_Neural_2015_CVPR_paper.pdf), CVPR'15.


# Summary
I stumbled upon this paper after reading this [Kaggle blog post](http://blog.kaggle.com/2015/09/29/grasp-and-lift-eeg-detection-winners-interview-2nd-place-daheimao/) about the 2nd place in the Grasp-and-Lift EEG Detection challenge.
The main idea of the paper is to use recurrent connections in the convolutional layers. 
This means **applying the same convolutional weights to the original input and the feature maps** of one time step before \\(T\\) times.

With this trick, one can increase the receptive field of the convolutions while keeping the number of parameters down (because of the shared weights).
Further, providing the input to all recurrent convolutions might help the gradient flow for learning.
This is also indicated by the comparison with recursive CNNs (applying the same convolutions \\(T\\) times but only to the previous feature maps and not to the original input).

The evaluations show state-of-the-art results on CIFAR-10, CIFAR-100, MNIST and SVHN.
However, it is interesting that Dropout is needed after the convolutional layers (except the last one) to really get good results.

A Caffe config of a single recurrent convolution layer looks like:
{% highlight protobuf %}
layer {
  name: "conv2"
  type: "Convolution"
  bottom: "norm1"
  top: "conv2"
  param {
    name: "conv2_w"
    lr_mult: 1
    decay_mult: 1
  }
  param {
    name: "conv2_b"
    lr_mult: 2
    decay_mult: 0
  }
  convolution_param {
    num_output: 96
    pad: 1
    kernel_size: 3
    stride: 1
    weight_filler {
      type: "gaussian"
      std: 0.02
    }
    bias_filler {
      type: "constant"
    }
  }
}
layer {
  name: "relu2"
  type: "ReLU"
  bottom: "conv2"
  top: "relu2"
}
layer {
  name: "norm2"
  type: "LRN"
  bottom: "relu2"
  top: "norm2"
  lrn_param {
    local_size: 13
    alpha: 0.001
    beta: 0.75
  }
}
layer {
  name: "conv2a"
  type: "Convolution"
  bottom: "norm2"
  top: "conv2a"
  param {
    name: "conv2rec_w"
    lr_mult: 1
    decay_mult: 1
  }
  convolution_param {
    num_output: 96
    pad: 1
    kernel_size: 3
    stride: 1
    weight_filler {
      type: "gaussian"
      std: 0.02
    }
    bias_term: false
  }
}
layer {
  name: "eltwise2a"
  type: "Eltwise"
  bottom: "conv2"
  bottom: "conv2a"
  top: "eltwise2a"
  eltwise_param {
    operation: SUM
  }
}
layer {
  name: "relu2a"
  type: "ReLU"
  bottom: "eltwise2a"
  top: "eltwise2a"
}
layer {
  name: "norm2a"
  type: "LRN"
  bottom: "eltwise2a"
  top: "norm2a"
  lrn_param {
    local_size: 13
    alpha: 0.001
    beta: 0.75
  }
}
layer {
  name: "conv2b"
  type: "Convolution"
  bottom: "norm2a"
  top: "conv2b"
  param {
    name: "conv2rec_w"
    lr_mult: 1
    decay_mult: 1
  }
  convolution_param {
    num_output: 96
    pad: 1
    kernel_size: 3
    stride: 1
    weight_filler {
      type: "gaussian"
      std: 0.02
    }
    bias_term: false
  }
}
layer {
  name: "eltwise2b"
  type: "Eltwise"
  bottom: "conv2"
  bottom: "conv2b"
  top: "eltwise2b"
  eltwise_param {
    operation: SUM
  }
}
layer {
  name: "relu2b"
  type: "ReLU"
  bottom: "eltwise2b"
  top: "eltwise2b"
}
layer {
  name: "norm2b"
  type: "LRN"
  bottom: "eltwise2b"
  top: "norm2b"
  lrn_param {
    local_size: 13
    alpha: 0.001
    beta: 0.75
  }
}
layer {
  name: "conv2c"
  type: "Convolution"
  bottom: "norm2b"
  top: "conv2c"
  param {
    name: "conv2rec_w"
    lr_mult: 1
    decay_mult: 1
  }
  convolution_param {
    num_output: 96
    pad: 1
    kernel_size: 3
    stride: 1
    weight_filler {
      type: "gaussian"
      std: 0.02
    }
    bias_term: false
  }
}
layer {
  name: "eltwise2c"
  type: "Eltwise"
  bottom: "conv2"
  bottom: "conv2c"
  top: "eltwise2c"
  eltwise_param {
    operation: SUM
  }
}
layer {
  name: "relu2c"
  type: "ReLU"
  bottom: "eltwise2c"
  top: "eltwise2c"
}
layer {
  name: "norm2c"
  type: "LRN"
  bottom: "eltwise2c"
  top: "norm2c"
  lrn_param {
    local_size: 13
    alpha: 0.001
    beta: 0.75
  }
}
layer {
  name: "drop2"
  type: "Dropout"
  bottom: "norm2c"
  top: "drop2"
  dropout_param {
    dropout_ratio: 0.4
  }
}
{% endhighlight %}


# Thoughts
I really like the basic idea of recurrent convolutional layers.
However, for me it is not completely clear how much of the performance is contributed to the recurrent connections.
I mean, why is a global max pooling used instead of fully-connected layers at the end?
Or why is Dropout after the recurrent convolutional layers improving the results drastically?
