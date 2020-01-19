---
layout: none
title:  "OctNetFusion: Learning Depth Fusion from Data"
teaser: "/images/teaser/octnetfusion.png"
authors: "Gernot Riegler, Ali Osman Ulusoy, Horst Bischof, Andreas Geiger"
conference: 3DV
year: 2017 (oral)
comments: false
---

In this paper, we present a learning based approach to depth fusion, i.e., dense 3D reconstruction from multiple depth images. 
The most common approach to depth fusion is based on averaging truncated signed distance functions, which was originally proposed by Curless and Levoy in 1996.
While this method is simple and provides great results, it is not able to reconstruct (partially) occluded surfaces and requires a large number frames to filter out sensor noise and outliers. 
Motivated by the availability of large 3D model repositories and recent advances in deep learning, we present a novel 3D CNN architecture that learns to predict an implicit surface representation from the input depth maps.
Our learning based method significantly outperforms the traditional volumetric fusion approach in terms of noise reduction and outlier suppression.
By learning the structure of real world 3D objects and scenes, our approach is further able to reconstruct occluded regions and to fill in gaps in the reconstruction.
We demonstrate that our learning based approach outperforms both vanilla TSDF fusion as well as TV-L1 fusion on the task of volumetric fusion.
Further, we demonstrate state-of-the-art 3D shape completion results.


[Paper](https://arxiv.org/abs/1704.01047)
[Code](https://github.com/griegler/octnetfusion)
[Poster](/papers/octnetfusion_poster.pdf)
[Slides](/papers/octnetfusion_slides.pdf)
