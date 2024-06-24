---
layout: post
type: project
title: Mapping lost rights of way
date: 2022-08-02 00:00:00 +0000
description: A Python geospatial data analysis
img: prow/thumb4.png # Add image post (optional)
tags: [research, data] # add tag
---

A land access research project to automatically analyse all footpaths in England and Wales to reclaim public rights of way (PRoW) using analysis of public GPX traces. 

Check out the [online map here](https://andrewwango.github.io/prow-map/), which shows GPS activity recorded by the public in Bedford and Central Bedfordshire up to 2013.

[![](https://img.shields.io/badge/🗺️-Online%20map-blue)](https://andrewwango.github.io/prow-map/)
[![](https://img.shields.io/badge/GitHub-Code-green?logo=GitHub)](https://github.com/Andrewwango/prow-map)
[![](https://img.shields.io/badge/🌐-Published%20article-blue)](https://earth.org/data_visualization/uk-land-access-rights/)

## Background

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

## Reclaiming public rights of way using public data

A more systematic data-driven approach is to use data of publicly-recorded GPS traces, for example from walking, running or cycling, which can expose potential paths of interest. We disregard any legal or historical information: **if the public are using the path, it should be a right of way**. This approach is desirable, since it is:

- Centered around how the public are interacting with paths.
- Automated and comprehensive: it is extremely easy to scale to analysing the whole country.

It also can complement the [aims of the Ramblers project](https://www.ramblers.org.uk/get-involved/campaign-with-us/dont-lose-your-way-2026/how-the-ramblers-are-working-to-save-lost-paths.aspx):
- To prioritise those paths which add the most benefit for people by highlighting high-activity areas.
- Supplement historical evidence with data about how well-used the paths actually are.

Additionally, this can also achieve the exact inverse of the main aim: to find paths that are currently rights of way but are not being used by the public: overgrown paths and barbed wire.

## Datasets

- **Public data**: A good source of public GPS activity (e.g. walking, cycling, driving) is provided by the OpenStreetMap (OSM) [API](https://wiki.openstreetmap.org/wiki/API_v0.6#GPS_traces), which delivers anonymised tracks in a given region. We use an [agglomerated dump of this data](http://zverik.openstreetmap.ru/gps/files/extracts/europe/great_britain/index.html) from 2013 to speed up data download.

- **Right of Way data**: A dataset of public rights of way from the definitive maps of each authority is kindly shared [here](https://www.rowmaps.com/) in one convenient API. Currently data for 121 authorities in England and Wales is available, see [here](https://www.rowmaps.com/gpxs/).

- **Base path network**: A comprehensive (private and public) path network, onto which the above datasets are overlaid, is available from [OpenStreetMap](openstreetmap.org/).

## Algorithm

The aim here is to combine the data detailing public usage of paths with the PRoW data into a single geodataset of paths to be displayed. The algorithm is easily run for all regions of England and Wales.

1. Map-match public GPS dataset and PRoW dataset to OSM path network using [`osmnx`](https://osmnx.readthedocs.io), to remove traces that are spurious or on highways.
2. Join path datasets using `geopandas`. Label paths with agglomerated measure of "activity".
3. Filter and smooth using `networkx`.
4. Query paths with non-zero activity but are not RoW from geodataset. Render colour-coded paths over an OSM map using `leaflet.js`.

Find the code on [GitHub](https://github.com/Andrewwango/prow-map) and try running your own analysis with the [demo notebook](https://github.com/Andrewwango/prow-map/demo.ipynb).

## Limitations and extensions

1. Roadside high-activity paths should be removed.
2. Paths on open access land should be removed.
3. Close path segments should be linked.
4. A newer source of data should be used, such as [Strava Metro](https://metro.strava.com/).
5. All analysed paths are limited to paths which appear on the OSM network. 
6. Anonymised data means it's harder to track how and when the public are using the paths.
7. Further geospatial analysis or machine learning using features from OSM IDs.

## Ethical considerations
All input public data is anonymised and untraceable as per the OSM API.

## Citation

Wang, Andrew. _Mapping lost rights of way: a Python geospatial data analysis_, 2024. URL: https://andrewwango.github.io/prow-map