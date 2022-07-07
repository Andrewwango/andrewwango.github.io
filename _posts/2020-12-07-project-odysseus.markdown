---
layout: post
title: Computer vision for social distancing monitoring
date: 2020-12-07 00:00:00 +0000
description:  # Add post description (optional)
img: turing/fig6.png # Add image post (optional)
tags: [research, data-science, machine-learning] # add tag
---

[![](https://img.shields.io/badge/arXiv-Paper%20in%20Preprint-green?logo=arxiv)](https://arxiv.org/abs/2012.07751)

Summary of my research with the Alan Turing Institute under Project Odysseus – understanding London ‘busyness’ and exiting lockdown. Read our paper ![here](https://arxiv.org/abs/2012.07751). Find more here on the [Turing website](https://www.turing.ac.uk/research/research-projects/project-odysseus-understanding-london-busyness-and-exiting-lockdown).


My contribution: designing, building and evaluting a real-time robust batch feature extraction and camera calibration tool for traffic cameras across 1000 locations in London. This was used to automatically map vehicles and pedestrians and was integrated into existing work on live traffic pollution monitoring and COVID-19 social distancing monitoring in conjunction with Transport for London.

Check out some visuals as a result of our work:
![](https://www.turing.ac.uk/sites/default/files/inline-images/jamcam_frontend_example.PNG)
![](https://www.turing.ac.uk/sites/default/files/inline-images/fig6.png)

Excerpt from the paper:

> **1 Camera Calibration** Obtaining a world-plane mapping of a camera scene is extensively described in the computer vision literature. A large portion of literature requires manual calibration using known patterns to estimate the transformation [2, 7, 23]. Vanishing line estimation is essential for perspective transformation [4]. [18, 6] use the activity of a large number of vehicles travelling parallel and regularly to find the vanishing point. [10, 22, 5, 8] calibrate the camera using clear, regular or known lines in the scene, which is not practical for the case of a large spread of different cameras. The stratified transformation discussed in [11] relies on the fact that there are many lines to be extracted from high quality images to build a real-world model. [18], [22], [5] and [3] extract visible road features by using a derivative-based binarisation operator. This is only suitable for cameras overlooking straight and visually similar lanes. Overall, our method is more easily generalised to higher quantity of cameras with cluttered urban traffic scenes and lower resolution. 
>
> The mapping, `(u,v,0) → (X,Y,Z)`, from the image plane to world geometry is sought, where there is no _a priori_ truth of the camera parameters. The _intrinsics_ (focal length, principal point, skew and aspect ratio) and _extrinsics_ (positioning and direction) therefore must be estimated or assumed. The cameras have the following limitations: Roads have non-zero curvature or have junctions and vary in width; Irregular road markings of varying quality; Cameras have low resolution, changing lighting in very short sample duration. To maintain robustness we make the following internal camera assumptions: **(a)** unit aspect ratio and constant skew; **(b)** coincidence of principal point and image centre; these are commonplace and rarely estimated due to lack of visual information [4], [6]. External assumptions are as following; **(c)** zero radial distortion; **(d)** flat horizon `v0 = v1`; **(e)** zero-incline road `Z = 0`; these seem reasonable by manual inspection of 100 random cameras and must be made given the above limitations. If cameras where these assumptions do not hold, a pre-processing stage using additional information can be implemented to correct radial distortion [6], inclined horizon (setting `v1 != v0`), and non-zero inclination `Z` [19].
>
> This simplified pinhole camera model allows the transformation to be described by four parameters `u0,v0,u1,h` where `(u0,v0),(u1,v0)` are the vanishing points of two orthogonal planar directions subtending the horizon line, and `h` is the height of the camera above ground (Figure 1). Parallel lines on the road and on cars, such as road edges, advanced stop lines and car and truck edges, are used to estimate this transformation (Figure 2).
>
>The Canny edge detector [21] is applied per frame to find sets of _road edges_ and _road perpendiculars_ as shown in Figure 2. The Hough transform matches collinear edge segments into linked lines which are then filtered by gradient[18] and dimensions. The vanishing point is then simply the maximum histogram density estimate of the pairwise line intersections. This is chosen over more expensive MLE methods [24] where the vanishing point error is optimised using least squares [4], [3] or Levenberg–Marquardt [18], [11]. This procedure is repeated across different contrast factors to provide a robust line detector in challenging lighting conditions. Finally, `u0,u1,v0` values are averaged over all frames to extract maximum information when the videos are sparsely populated with vehicles. Finally, the camera height h can be manually calculated by transforming an object of known dimensions. For example, using frequently appearing London buses of fixed 2.52m width, the calculated height averages `h = 9.6m` with 10% average deviation across 7 randomly picked cameras. Other ways to obtain the scale `h` include using car length averages [19] or known lane spacings [8, 3].
