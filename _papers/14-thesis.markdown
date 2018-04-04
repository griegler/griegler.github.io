---
title:  "Deep Learning for 2.5D and 3D"
teaser: "/img/teaser/thesis.png"
authors: "Gernot Riegler"
conference: 
year: 2017
comments: false
---

<details>
<summary>
Deep learning based method are revolutionizing many fields in computer science, especially in computer vision, speech recognition and natural language processing. 
These methods have in common that they learn a hierarchy of non-linear feature extractors together with a classifier, or regressor in an end-to-end fashion.
Although the underlying concepts, especially artificial neural networks and the backpropagation algorithm, are several decades old, they came to new importance mainly due to today's sheer amount of available data and parallel compute power, i.e., GPGPUs.
The applications in computer vision mainly focus on recognition tasks on natural images which are 2D projections of the world.
In contrast, in this thesis we propose methods that investigate deep learning specifically for 2.5D and 3D data.
</summary>

2.5D data can be understood as a 2D image that has a depth value associated with each pixel.
There exists now a wide range of sensor technologies that enables the fast and cheap recording of such depth maps.
However, most of those recordings are influenced by noise and have a low spatial resolution.
We propose a novel technique that combines deep convolutional networks with a variational model to tackle this depth super-resolution problem, i.e., a method that increases the spatial resolution and simultaneously reduces the influence of the noise.
As it is difficult to obtain high-resolution, high-quality depth maps as training data for this task, we optimize our joint model in an end-to-end fashion on a large corpus of synthetically generated data.
In an extensive evaluation on three benchmark datasets, we validate our method that significantly outperforms state-of-the-art methods.

Deep learning on volumetric 3D data faces one crucial problem that is independent of its application:
The memory consumption increases cubically with respect to the input resolution, whereas the memory of GPGPUs is limited.
We propose in this thesis a drop-in solution based on an efficient space partitioning data structure. 
Instead of a regular voxel grid, we utilize an octree within the network to focus memory and computation on more relevant regions of the input.
With this new technique, we are able to increase the input resolution by at least a factor of x64 without losing the representational power of the convolutional network.
Further, we show a series of tasks where a detailed representation of the 3D input is absolutely beneficial, i.e., the performance increases simply by increasing the input resolution.

An alleged drawback of this method might be that the space partitioning has to be known in advance.
Hence, we also show in this thesis how we can learn the splitting of the octree along with a volumetric 3D reconstruction to circumvent the problem. 
We subsequently utilize this method for volumetric depth fusion and volumetric depth completion.
For the former, our method outperforms established baselines, especially on difficult settings where we have only a low number of input views, or severe input noise.
For the latter, i.e., predicting the whole 3D scene from a single depth input, we achieve new state-of-the-art results.
</details>




[Thesis](https://www.dropbox.com/s/rlug24f2kfgmtz5/thesis.pdf?dl=0)
