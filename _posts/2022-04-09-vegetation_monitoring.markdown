---
layout: post
title: Forest vegetation quantification for environmental monitoring using hand-held cameras
date: 2022-04-09 00:00:00 +0000
description:  # Add post description (optional)
img: vegetation.jpg # Add image post (optional)
tags: [research, machine-learning, cambridge] # add tag
---

[![](https://img.shields.io/badge/GitHub-View%20on%20GitHub-blue?logo=GitHub)](https://github.com/Andrewwango/vegetation-segmentation)

Summary of my project for the 4M25 Advanced Robotics Final Technical Report as part of the MEng 4th year course at Cambridge. Find the full report [here](https://andrewwango.github.io/assets/pdf/4M25_Report_2_web.pdf).

## Report Abstract
Automatic vegetation mapping in dense forest areas is desirable for a number of environmental reasons, allowing non-technical users and robots to efficiently monitor local natural environments for better forest management. We propose a computer vision model which quantifies videos taken from walking around a forest to produce a vegetation score at each point. We show that this can be done by efficiently training neural networks for depth estimation and semantic segmentation to understand the forest image scenes. We train and evaluate on a forest image dataset from the literature. The model achieves high correlation with human-labelled vegetation scores on a sample test video and low error on the image networks on the validation set. 

All code and experiments can be found on ![GitHub](https://github.com/Andrewwango/vegetation-segmentation).

## Motivation
