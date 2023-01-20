---
layout: post
type: project
title: NI schools computer studies data analysis
date: 2023-01-20 00:00:00 +0000
description: 
img: 
tags: [data] 
---

## Background

[The Software Alliance, Northern Ireland](https://softwarealliancenorthernirelan.godaddysites.com/about) exists to lobby and drive strategy and policy development to ensure that Northern Ireland becomes the world leading region for innovative software.  

The Software Alliance acknowledges the inequity of access and low uptake of computing education in primary and post-primary schools in Northern Ireland. To tackle the computing education challenges, The Software Alliance Board will conduct a landscape review of the education ecosystem.  

At Kainos, a company headquartered in Belfast and a member of the alliance, we recognise that computing education is important for our success. Alongside our [other outreach activities](https://www.kainos.com/insights/news/kainos-tech-outreach-programme-receives-highly-commended-honour-responsible-business-awards), a first step is analysing the data of current and past computing education in Northern Ireland.

## Methods

Given the available data, the task is to ask questions to tell a story about the state of Computing Studies (CS) education in Northern Ireland (NI), in Key Stages (KS) 4 and 5 (ages 14-18), representing GCSE and A-Level qualifications. We also see how it compares with other subjects such as Information and Communications Technology (ICT), a more well-known qualification that is less relevant for aspiring tech innovators.

The following data sets were made available:

- List of all CS and ICT delivered courses by school and year group in 2021-2022 for years 11-14 in Northern Ireland, from [Entitlement Framework](https://www.education-ni.gov.uk/articles/entitlement-framework).
- Table of all GCSE and A Level exam entries and results by subject, from years 2015-2016 to 2020-2021 in Northern Ireland, from [RM Education](https://www.rm.com/).

Values were extracted from the PDF tables, cleaned using `python` and joined with postcode data of NI schools. The data analysis was performed in Tableau.

## Results

Below are some of the results included in the analysis. Each section asks a question that informs the data analysis. Hover over and click into the charts and maps to get more insight into the data.

### How does engagement differ between Computer Studies and ICT?

In 2021-2022, the total number of ICT pupils is much bigger than the total number of Computer Studies pupils for both Key Stages 4 and 5.

<iframe
  src="https://andrewwango.github.io/assets/html/ni_outreach/Total_Pupils.html"
  style="width:100%;"
></iframe>

### What are the regional differences in teaching availability in NI?

In 2021-2022, those schools offering Computer Studies are poorly distributed around NI, compared to those offering ICT. Note circle size represents number of pupils per school.

<iframe
  src="https://andrewwango.github.io/assets/html/ni_outreach/Maps.html"
  style="width:100%;"
></iframe>

Computer studies:


### What courses are on offer?


### How have course numbers changed since 2015?



### 


<iframe
  src="https://andrewwango.github.io/assets/html/ni_outreach/Map_ICT.html"
  style="width:100%;"
></iframe>