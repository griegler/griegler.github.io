---
title:  "Connecting the Dots: Learning Representations for Active Monocular Depth Estimation"
teaser: "/images/teaser/connecting_the_dots.jpg"
authors: "Gernot Riegler, Yiyi Liao, Simon Donne, Vladlen Koltun, Andreas Geiger"
conference: CVPR
year: 2019 (poster)
comments: false
---

We propose a technique for depth estimation with a monocular structured-light camera, i.e., a calibrated stereo set-up with one camera and one laser projector. Instead of formulating the depth estimation via a correspondence search problem, we show that a simple convolutional architecture is sufficient for high-quality disparity estimates in this setting. As accurate ground-truth is hard to obtain, we train our model in a self-supervised fashion with a combination of photometric and geometric losses. Further, we demonstrate that the projected pattern of the structured light sensor can be reliably separated from the ambient information. This can then be used to improve depth boundaries in a weakly supervised fashion by modeling the joint statistics of image and depth edges. The model trained in this fashion compares favorably to the state-of-the-art on challenging synthetic and real-world datasets. In addition, we contribute a novel simulator, which allows to benchmark active depth prediction algorithms in controlled conditions.


[Paper](http://openaccess.thecvf.com/content_CVPR_2019/papers/Riegler_Connecting_the_Dots_Learning_Representations_for_Active_Monocular_Depth_Estimation_CVPR_2019_paper.pdf)
[Supplemental Material](http://openaccess.thecvf.com/content_CVPR_2019/supplemental/Riegler_Connecting_the_Dots_CVPR_2019_supplemental.pdf)
[Code](https://github.com/autonomousvision/connecting_the_dots)
