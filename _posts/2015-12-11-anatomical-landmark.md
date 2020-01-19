---
layout: none
title:  "Anatomical landmark detection in medical applications driven by synthetic data"
teaser: "/images/teaser/anatomical-landmark.png"
authors: "Gernot Riegler, Martin Urschler, Matthias Rüther, Horst Bischof, Darko Stern"
conference: TASK-CV
year: 2015 (poster)
comments: false
---

An important initial step in many medical image analysis applications is the accurate detection of anatomical landmarks. Most successful methods for this task rely on data-driven machine learning algorithms. However, modern machine learning techniques, e.g. convolutional neural networks, need a large corpus of training data, which is often an unrealistic setting for medical datasets.In this work, we investigate how to adapt synthetic image datasets from other computer vision tasks to overcome the under-representation of the anatomical pose and shape variations in medical image datasets. We transform both data domains to a common one in such a way that a convolutional neural network can be trained on the larger synthetic image dataset and fine-tuned on the smaller medical image dataset. Our evaluations on data of MR hand and whole body CT images demonstrate that this approach improves the detection results compared to training a convolutional neural network only on the medical data. The proposed approach may also be usable in other medical applications, where training data is scarce.

[Paper](/papers/anatomical-landmark.pdf)
