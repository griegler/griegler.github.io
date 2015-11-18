---
layout: post
title:  "Summary: Seven ways to improve example-based single image super resolution"
comments: true
date:   2015-11-10 16:00:00
categories: summary paper super-resolution
---

[Link to the paper](http://arxiv.org/abs/1511.02228).


# Summary
As the title suggests, the paper presents seven heuristics to improve example-based single image super-resolution (SISR) methods. 
The heuristics are quite general, so the should be applicable to any example-based SISR method, however, they are mainly evaluated on the authors own A+ method.
For this method, the heuristics improves the PSNR results by 0.62dB on average.

The seven heuristics are:

1. Augmentation of the training data. 
The size of the dataset is increased by scaling, rotating and flipping the images.
2. Larger dictionary and hierarchical search. 
This heuristic is only valid for sparse coding approaches. 
By increasing the size of the sparse coding dictionary, the method generalizes better.
To decrease the search time for A+ a simple hierarchical cluster of the anchors is performed.
3. Back projection. 
[Irani and Peleg](http://www.cse.huji.ac.il/course/2003/impr/supres-cvgip-gm91.pdf)
4. Cascade of anchored regressors.
The idea is to train the same model several times (stage wise), but the input of model \\(N\\) is the output of model \\(N-1\\).
5. Enhanced prediction.
The low-resolution input gets flipped and rotated and the model is applied to all 8 images.
Then the output is the average of the back-transformed outputs. 
This heuristic is especially useful when a cascade is utilized.
6. Self-similarities.
If the image contains repetitive structures (urban facades, ...), then building an internal dictionary for each image might be beneficial.
7. Reasoning with context.
Take for each patch a larger patch and cluster them in four regions.
The anchors of A+ are then trained for each region to include the context idea.



# Thoughts
Although, some ideas are specific towards the sparse coding and the A+ method, the heuristics might be useful for other methods too.
In the final benchmark results, it would have been interesting to see the heuristics also applied to the other methods and not only A+.
