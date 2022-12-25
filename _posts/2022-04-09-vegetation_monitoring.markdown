---
layout: post
title: Forest vegetation quantification for environmental monitoring using hand-held cameras
date: 2022-04-09 00:00:00 +0000
description:  # Add post description (optional)
img: vegetation.jpg # Add image post (optional)
tags: [research, machine-learning, cambridge, robotics] # add tag
---

[![](https://img.shields.io/badge/GitHub-View%20on%20GitHub-blue?logo=GitHub)](https://github.com/Andrewwango/vegetation-segmentation)

Summary of my project for the 4M25 Advanced Robotics Final Technical Report as part of the MEng 4th year course at Cambridge. Find the full report [here](https://andrewwango.github.io/assets/pdf/4M25_Report_2_web.pdf).

## Report Abstract
Automatic vegetation mapping in dense forest areas is desirable for a number of environmental reasons, allowing non-technical users and robots to efficiently monitor local natural environments for better forest management. We propose a computer vision model which quantifies videos taken from walking around a forest to produce a vegetation score at each point. We show that this can be done by efficiently training neural networks for depth estimation and semantic segmentation to understand the forest image scenes. We train and evaluate on a forest image dataset from the literature. The model achieves high correlation with human-labelled vegetation scores on a sample test video and low error on the image networks on the validation set. 

All code and experiments can be found on ![GitHub](https://github.com/Andrewwango/vegetation-segmentation).

## Motivation
Vegetation mapping and quantification is an important task in many fields of practical local environmental monitoring, such as for:

- Deforestation <img src="{{site.baseurl}}/assets/img/vegetation/Picture1.jpg" alt="drawing" width="20%"/>
- Conservation and rewilding <img src="{{site.baseurl}}/assets/img/vegetation/Picture2.jpg" alt="drawing" width="20%"/>
- Natural disasters <img src="{{site.baseurl}}/assets/img/vegetation/Picture1.jpg" alt="drawing" width="20%"/>

The above are _local_ applications, and often require ground-level imagery to be useful, as opposed to satellite imagery:

<img src="{{site.baseurl}}/assets/img/vegetation/Picture4.jpg" alt="drawing" width="20%"/> <img src="{{site.baseurl}}/assets/img/vegetation/Picture5.jpg" alt="drawing" width="20%"/>

Non-technical researchers and robots may wish to automatically quantify vegetation in given hand or robot-recorded video scenes. This can be used to compare vegetation levels from time to time in forest and other natural environments, or by combining GPS data to produce vegetation heatmaps. This removes the time-consuming and laborious need to manually quantify vegetation; see the [full report](https://andrewwango.github.io/assets/pdf/4M25_Report_2_web.pdf) for an analysis.

## Approach
We develop a computer vision model to solve this robotics task. This consists of a mathematical model to quantify the “vegetation levels” in an unstructured forest scene, where object locations and sizes are not well-defined, unlike urban scenes. Then, given videos taken by a hand-held camera as one walks through forest paths or by an autonomous robotic vehicle, our model detects and quantifies vegetation present per frame to record the total vegetation presented during the video.

The model works as follows:

- Input frame at given time ![]({{site.baseurl}}/assets/img/vegetation/Picture6.jpg)
- Detect frame perspective ![]({{site.baseurl}}/assets/img/vegetation/Picture8.jpg)
- Segment vegetation from frames ![]({{site.baseurl}}/assets/img/vegetation/Picture7.jpg)
- Agglomerate vegetation into one number per frame.

See the full report for full model details and implementation.

## Results
Input video:
<img src="{{site.baseurl}}/assets/img/vegetation/orig_images.gif" alt="drawing" width="30%"/>

Estimated depths:
<img src="{{site.baseurl}}/assets/img/vegetation/depth_images.gif" alt="drawing" width="30%"/>

Semantic segmentation:
<img src="{{site.baseurl}}/assets/img/vegetation/preds.gif" alt="drawing" width="30%"/>

Quantity of grass:
<img src="{{site.baseurl}}/assets/img/vegetation/VI_grass.gif" alt="drawing" width="30%"/>

Quantity of vegetation:
<img src="{{site.baseurl}}/assets/img/vegetation/VI_veg.gif" alt="drawing" width="30%"/>
)