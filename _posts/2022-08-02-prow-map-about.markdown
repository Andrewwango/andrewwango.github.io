---
layout: post
type: project
title: Mapping lost rights of way
date: 2022-08-02 00:00:00 +0000
description: A Python geospatial data analysis
img: prow/thumb4.png # Add image post (optional)
tags: [research, data] # add tag
---

A project to automatically analyse all footpaths in England and Wales to reclaim public rights of way (PRoW) using analysis of public GPX traces. In conjunction with [Joe Thorogood](https://rowresearch.coventry.domains/contact/).

[Code](https://github.com/Andrewwango/prow-ml) | [Published article](https://earth.org/data_visualization/uk-land-access-rights/) | [Web app](https://andrewwango-prow-ml-web-app-tz9rk4.streamlit.app/)

## Introduction

> The majority of the English countryside is out of bounds for most of its population. 92% of the countryside and 97% of rivers are off limits to the public.

_From [Right to Roam](https://www.righttoroam.org.uk/)._

We need to reclaim paths for the public, by identifying paths that should be rights of way. Why?

> A 'Right of Way', often called a highway, exists if there is 'a public right to to pass and re-pass along a defined route'. It is a legal term for land that is accessible for the public even if it crosses private land.
> The 2000 Countryside and Rights of Way Act, states that Surveying Authorities (an authority in charge of a Definitive Map and Statement of Public Rights of Way) will no longer be able to accept applications to register historical routes after the 31st December 2025. There are many footpaths, bridleways and byways that remain unregistered: some estimates suggest 1000s of kilometers of footpath are at risk. The race is on to record the nation’s unregistered routes before the 1st of January 2026. After this date, unregistered Public Rights of Way will be lost forever.

_From [Right of Way Research](https://rowresearch.coventry.domains/). See [examples](https://rowresearch.coventry.domains/blog-2/)._

The Ramblers are tackling this by creating a [map of public rights of way that may have been lost](https://dontloseyourway.ramblers.org.uk/):

> We've searched all of England and Wales and found over 49,000 miles of paths that could be lost forever, unless we come together to save them. 

> Our paths are one of our most precious assets, hidden in plain sight, and often taken for granted, they allow everyone to enjoy the countryside, both on our doorstep and across Britain’s iconic landscapes. 

> With the help of thousands of volunteers we searched all of England and Wales and found over 49,000 miles of paths which could be lost forever. Time is running out, with only five years left to collect the historical, documentary evidence needed to build and submit applications to restore the most important paths for future generations. 

_From [Ramblers](https://www.ramblers.org.uk/get-involved/campaign-with-us/dont-lose-your-way-2026.aspx). Watch [this talk](https://www.youtube.com/watch?v=N0oSG4iEy0Q&list=PLJsLOysi1d5Ebb_Gxvk1Kuck5dYD6P0HW) for an excellent explanation of the injustice and their work._

A more systematic approach is available using data of publicly-recorded GPS traces, for example from walking, running or cycling, which can expose potential paths of interest. As a data-oriented approach, we disregard any legal or historical information: **if the public are using the path, it should be a right of way**. This approach is desirable, since it is:

- Centered around how the public are interacting with paths.
- Automated and comprehensive: it is extremely easy to scale to analysing the whole country.

It also can complement the [aims of the Ramblers project](https://www.ramblers.org.uk/get-involved/campaign-with-us/dont-lose-your-way-2026/how-the-ramblers-are-working-to-save-lost-paths.aspx):

>  Identifying potential lost rights of way is just the start of a long process to put them back on the map. There are four more steps to saving them:
>
> - Prioritise those paths which add the most benefit for people.

This task can be automated given the paths dataset and knowledge of the greater path network.

> - Research individual paths to find out if they can be saved.
> - Build applications based on historical evidence.

Evidence can be supplemented with data about how well-used the paths actually are.

> - Submit applications by 1st January 2026.

### Other aims

The exact complement of the main aim is to find paths that are currently rights of way but are not being used by the public: overgrown paths and barbed wire. These are exposed in the web-app below.

### Extensions

- Can we use further descriptive statistics or machine learning to prioritise detected paths?

## Datasets

- **Public data**: A good source of public GPS activity (e.g. walking, cycling, driving) is provided by the OpenStreetMap (OSM) [API](https://wiki.openstreetmap.org/wiki/API_v0.6#GPS_traces), which delivers anonymised tracks in a given region. We use an [agglomerated dump of this data](http://zverik.openstreetmap.ru/gps/files/extracts/europe/great_britain/index.html) from 2013 to speed up data download. In future it would be nice to use a more modern source such as [Strava Metro](https://metro.strava.com/).

- **Right of Way data**: A dataset of public rights of way from the definitive maps of each authority is kindly shared [here](https://www.rowmaps.com/) in one convenient API. Currently data for 121 authorities in England and Wales is available, see [here](https://www.rowmaps.com/gpxs/).

- **Base path network**: A comprehensive path network, onto which the above datasets are overlaid, is available from OSM. This includes all public and private paths that have made it onto [OSM](openstreetmap.org/). A dataset containing only paths (and not roads) is downloaded using [OSMNX](https://osmnx.readthedocs.io). 

## Algorithm

The aim here is to combine the data detailing public usage of paths with the PRoW data into a single geodataset of paths to be displayed. The algorithm is easily run for all regions of England and Wales.

1. Map-match public GPS dataset and PRoW dataset to OSM path network using `osmnx`, to remove traces that are spurious or on highways.
2. Join path datasets using `geopandas`. Label paths with measure of "activity".
3. Filter and smooth using `networkx`.
4. Query paths with non-zero activity but are not RoW from geodataset. Render colour-coded paths over an OSM map using `folium`.

## Deliverables

1. A geodataset of path entries labelled with PRoW (yes/no) and public activity, and tagged with OSM IDs for further feature analysis.
2. An online map presenting the data stored on server, showing analysed paths.

The online map is available on the [web-app](https://andrewwango.github.io/prow-web-app) - check it out!. An example is shown below:

<iframe
  src="https://andrewwango.github.io/assets/html/Beds_EO.html"
  style="width:100%; height:300px;"
></iframe>

_Interactive map showing GPS activity recorded by the public (such as walking, running and cycling) in Bedford and Central Bedfordshire up to 2013. Black represents activity data that coincides with public rights of way, that is, where the activity was legal. Red/magenta represents activity data that does not, that is, where the activity counted as trespass. Deeper red indicates higher activity levels._

## Limitations

1. Roadside foot- and cycle-paths show up as high activity non-RoW: these should be removed.
2. Need to remove all paths intersecting with open access land and other public land.
3. Need to link close path segments.
4. Current analysis uses public recorded GPS data from 2013 - I can't find any newer dumps than this.
5. All analysed paths are limited to paths which appear on the OSM network. 
6. Anonymised data means it's harder to track how and when the public are using the paths.