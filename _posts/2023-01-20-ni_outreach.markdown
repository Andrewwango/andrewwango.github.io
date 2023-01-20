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

Given the available data, the task is to tell a story about the state of computing (Computer Studies, CS) education in Northern Ireland (NI), in Key Stages 14 and 15 (ages 14-18), and how it compares with other subjects such as Information and Communications Technology (ICT), a more well-known qualification that is less relevant for aspiring tech innovators. The questions asked that inform our data analysis include:

- How does engagement differ between Computer Studies and ICT?
- What are the regional differences in teaching availability in NI?
- What courses are on offer?
- How have course numbers changed since 2015?

The following data sets were made available:

- List of all CS and ICT delivered courses by school and year group in 2021-2022 for years 11-14 in Northern Ireland, from [Entitlement Framework](https://www.education-ni.gov.uk/articles/entitlement-framework).
- Table of all GCSE and A Level exam entries and results by subject, from years 2015-2016 to 2020-2021 in Northern Ireland, from [RM Education](https://www.rm.com/).

Values were extracted from the PDF tables, cleaned using `python` and joined with postcode data of NI schools. The data analysis was performed in Tableau.

## Stories

### 


<iframe
  src="https://andrewwango.github.io/assets/html/ni_outreach/Map_ICT.html"
  style="width:100%; height:600px;"
></iframe>