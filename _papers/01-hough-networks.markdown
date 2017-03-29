---
title:  "Hough Networks for Head Pose Estimation and Facial Feature Localization"
teaser: "/img/teaser/hough_networks.png"
authors: "Gernot Riegler, David Ferstl, Matthias Rüther, Horst Bischof"
conference: BMVC
year: 2014 (poster)
comments: false
---

We present Hough Networks: a novel method that combines the idea of Hough Forests with Convolutional Neural Networks. Similar to Hough Forests, we perform a simultaneous classification and regression on densely-extracted image patches. But instead of a Random Forest we utilize a CNN which is capable of learning higher-order feature representations and does not rely on any handcrafted features. Applying a CNN at patch level allows the segmentation of the image into foreground and background. Furthermore, the structure of a CNN supports efficient inference of patches extracted from a regular grid. We evaluate the proposed Huogh Networks on two computer vision tasks: head pose estimation and facial feature localization. Our method achieves at least state-of-the-art performance without sacrificing versatility which allows extension to many other applications.

[Paper](/papers/hough-networks.pdf)
