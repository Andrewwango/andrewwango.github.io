---
layout: post
type: research
title: London social distance estimation
date: 2020-12-07 00:00:00 +0000
description: BCS Computer Journal paper with the Alan Turing Institute
img: turing/turing_cover.png 
tags: [research, data-science, machine-learning, internship] # add tag
---

[![](https://img.shields.io/badge/arXiv-Paper%20in%20Preprint-green?logo=arxiv)](https://arxiv.org/abs/2012.07751)

Summary of our paper ["Near Real Time Social Distance Estimation in London"](https://arxiv.org/abs/2012.07751), which has been accepted at the British Computer Society's Computer Journal.

Cite: James Walsh, Oluwafunmilola Kesa, Andrew Wang, Mihai Ilas, Patrick O'Hara, Oscar Giles, Neil Dhir, Mark Girolami, Theodoros Damoulas: _Near Real-Time Social Distancing in London_. arXiv:2012.07751.

Publications:

- [arXiv paper](https://arxiv.org/abs/2012.07751)
- [CIUK poster competition 2020 winner](https://www.scd.stfc.ac.uk/SiteAssets/Pages/CIUK-2020-Poster-Competition/O%27Hara.pdf)
- Summary of the project on the [Alan Turing Institute website](https://www.turing.ac.uk/research/research-projects/project-odysseus-understanding-london-busyness-and-exiting-lockdown): Project Odysseus – understanding London ‘busyness’ and exiting lockdown.
- [Press](https://www.businessweekly.co.uk/news/academia-research/cambridge-university-role-%E2%80%98london-after-lockdown%E2%80%99-odyssey)
- [Wider project statement](https://www.turing.ac.uk/research/impact-stories/helping-london-navigate-lockdown-safely)

## 1. Introduction

We studied robust object detection and camera calibration in 900 traffic cameras around London. We showed this can be used to monitor social distance in real-time around London, the busiest city in the UK. 

The paper also showed that we can develop an end-to-end solution that touches on multiple Machine Learning research areas using multiple data sources to benefit public health and for social good. The project was in collaboration with the [Alan Turing Institute](https://www.turing.ac.uk/) (the UK's national institute for Data Science and AI), the University of Cambridge ([us](http://www.eng.cam.ac.uk/)) and the University of Warwick. Research funding was from Lloyd’s Register Foundation.

## 2. Solution

Video footage is provided by Transport for London (TfL) from 900 low-resolution "JamCam" cameras spread across London, and can be viewed live at [this site](https://www.tfljamcams.net/). These images look like:

<img src="{{site.baseurl}}/assets/img/turing/jamcam example.jpg" alt="drawing" width="50%"/>

We use this to detect footfall and measure social distance statistics in real time for these locations around London, continually throughout the pandemic. Previous industrical solutions use, for example, Google movement data or point of sale transaction data which are severely limited. The below diagram shows our approach: object detection and physical distance estimation are fed into an API and live dashboard deployed on Azure.

<img src="{{site.baseurl}}/assets/img/turing/poster_fig1.png" alt="drawing" width="80%"/>

These methods tie in with other concurrent research projects, for example the Institute's [wider COVID approach](https://www.turing.ac.uk/research/impact-stories/helping-london-navigate-lockdown-safely) and [air quality monitoring project](https://www.turing.ac.uk/research/research-projects/london-air-quality). These projects integrate multiple large-scale heterogeneous datasets and develop ML models to infer mobility and transportation activity throughout London. The above diagram shows how this other data (e.g. on-the-ground traffic and footfall measurement) can be combined to provide forecasts and alerts.

There are many stages to the main inference pipeline proposed, an each stage is an interesting and ongoing research problem in itself:

<img src="{{site.baseurl}}/assets/img/turing/pipeline.png" alt="drawing" width="100%"/>

- Object detection (high accuracy, real-time inference and challenging conditions)
- World-plane transformation/camera calibration (no a-priori parameters, high robustness, no validation datasets)
- Group detection (graph theory problem)
- Social distance metric calculation
- Others, such as scene stability detection for change point alerting.

## 3. Results

The following images depict the successful implementation of the pipeline:

1. Object detection using YOLOv4 on a mixture of standard COCO and MIO-TCD and evaluated using our custom dataset (see below)

<img src="{{site.baseurl}}/assets/img/turing/fig2b.png" alt="drawing" width="60%"/>

2. Calibration involving robust camera perspective mapping and world-plane affine transformation (see below)

<img src="{{site.baseurl}}/assets/img/turing/fig2a.png" alt="drawing" width="60%"/>

3. Social distance clustering and aggregation produces metrics time-series at each location. Statistics we measured were total number of people, average inter-group “social” distance and average within-group distance. These statistics allowed us to see how lockdown and policies such as ”work from home” or “eat-out-to-help-out” affected “busyness”, and also specific examples where real local policy intervention such as pavement extension affected social distancing. See the paper for more details.

<img src="{{site.baseurl}}/assets/img/turing/fig8_zoom.png" alt="drawing" width="40%"/>

4. Dashboard deployed to Azure.

<img src="{{site.baseurl}}/assets/img/turing/fig10.png" alt="drawing" width="60%"/>

5. A quote from Transport for London:

> “TfL says that it implemented over 700 such interventions at the height of the pandemic’s first wave, and that the Turing’s tool provided key data for those decisions”


## 4. What is a Digital Twin

## 5. Deep dives

The following couple of sections go into a bit more depth about some of the interesting parts of the paper.

### 5.1 Camera calibration

### 5.2 Object detection

## 6. Ethical considerations

## 7. Future directions