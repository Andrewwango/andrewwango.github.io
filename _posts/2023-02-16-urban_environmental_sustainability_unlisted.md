---
layout: post
title: Comparing urban environmental sustainability indicators in Europe
date: 2023-02-04 00:00:00 +0000
type: unlisted
description: Unlisted copy of article at [earth.org](https://earth.org/data_visualization/urban-environmental-sustainability/) 
img: EO/green_cities_EO_cover.jpg
tags: [research, data] 
---

Cover photo by [Martin Magnemyr](https://unsplash.com/@mmagnemyr?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/photos/rXdnQundyOo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

**Author** Andrew Wang | Twitter: @andrewwango

## Summary

A city’s environmental sustainability can be measured using a vast set of indicators. Is it sensible to assess urban environmental sustainability with only a narrow set of these? After comparing various indicators across European cities, we conclude that some cities may perform well in one aspect but poorly in another and that cities must simultaneously consider many perspectives in order to ensure a truly environmentally sustainable future.

## Introduction

Cities that are best prepared for a "smart city future" should be sustainable, according to the recent 2022 [ProptechOS](https://proptechos.com/smart-city-index/) report which benchmarks cities in US and Europe on a selection of indicators. This is backed up by the [OECD smart cities definition](https://www.oecd.org/cfe/cities/Smart-cities-measurement-framework-scoping.pdf). In the report, sustainability is measured using a green infrastructure indicator across 46 European cities, combining: 

- Number of electric vehicle (EV) charging points per capita
- Number of green certified buildings according to [Green Building Information Gateway](https://www.gbig.org/) (GBIG) in 2022

This prompts the following questions. How do we measure the environmental sustainability of our cities? Do some cities perform well in one indicator but badly in others?

## How do we measure urban environmental sustainability?

Although they correlate with lower emissions, the numbers of EV charging points and green certified buildings measure environmental progress in a (current) model of urbanisation centred around cars and buildings. 

According to the [UN Habitat World Cities Report 2022](https://unhabitat.org/sites/default/files/2022/06/wcr_2022.pdf), it is important that the goal for a future city should place environmental sustainability at its core, however, we must consider a multitude of desirable outcomes to ensure that any solution benefits the planet and all inhabitants. As an example, electric cars can play only one part in a wider approach to sustainable urban mobility.

The [European Environment Agency (EEA)’s reports](https://www.eea.europa.eu/themes/sustainability-transitions/urban-environment) present an urban environmental sustainability framework that pulls together many different building blocks for a common goal, described through the lenses of a city that is [green, low-carbon, resilient, circular, inclusive and healthy](https://www.eea.europa.eu/themes/sustainability-transitions/urban-environment/urban-sustainability-in-europe/#:~:text=Lenses%20%E2%80%94%20perspectives%20in%20urban%20environmental%20sustainability). We will compare ProptechOS' "green infrastructure" indicator with the following factors:

- Sustainable mobility and infrastructure
- Energy efficiency and built environment quality
- Renewable energy and resource usage
- Environmental quality
- Green spaces and nature quality
- Zero waste

## How do different measures compare?
Other organisations have recently published indicators measuring the above urban environmental sustainability factors in cities around Europe. We look at how some of these published indicators compare to those published by ProptechOS.

We include 6 indicators published in the **[2019 SDG Index and Dashboards Report for European Cities](https://euro-cities.sdgindex.org/)**. These cover subsets of the UN [Sustainable Development Goals](https://sdgs.un.org/goals) (SDG) linked to urban environmental sustainability, originally across 45 European cities. We also include 3 indicators published in the **[Clean Cities Campaign 2022 rankings](https://cleancitiescampaign.org/ranking-2022-edition/)**. These are transparently and robustly researched indicators prioritising zero-emissions mobility, originally across 36 European cities.

**Click the dropdown to view the indicators.** See Appendix below for descriptions of all indicators used.

<iframe
  src="{{site.baseurl}}/assets/html/green_cities.html"
  style="width:100%; height:520px; border:0"
></iframe>

__Note that this is not designed to be a complete analysis of all European cities, and many originally studied cities have been omitted because of lack of data across datasets.__ To reproduce this analysis, see the [code](https://www.kaggle.com/code/andrewwang27/green-cities-analysis).


## Discussion

How do each of these indicators compare to the _ProptechOS_ measure of green fnfrastructure?

**Climate policies.** We observe a very strong positive trend, showing that the development of certain infrastructure is associated with strong climate-positive policy decisions with regard to other infrastructure, with cities such as London (United Kingdom) and Amsterdam (Netherlands) performing highly and Warsaw (Poland) and Prague (Czech Republic) performing poorly on both indicators.

**Access to climate-friendly mobility and space for people.** We notice a weak positive trend with notable outliers, showing that in some cities, sustainable mobility covers much more than just electric vehicles. For example, London (UK) is known for being poorly cyclable and suffers from high congestion, whereas Copenhagen (Denmark) has the most affordable public transport and is widely ranked among the most cyclable cities in the world.

**SDG15: Life on land.** This indicator measures the quality of natural habitats and the provision of green space in cities. We see an interesting positive and negative trend. Cities like Ljubljana (Slovenia) and Zagreb (Croatia) are at the top of SDG15 despite being lower on the Green Infrastructure scale, whereas cities considered more highly developed such as Amsterdam (Netherlands) or London (United Kingdom) perform worse in SDG15, showing a higher negative impact on the environment and ecology. One notable exception is Oslo (Norway), which is notably [prioritising biodiversity in the built environment](https://oppla.eu/casestudy/19231) as a rapidly expanding metropolitan area.

**Recycling rate.** We see a fairly strong positive trend, showing that cities prioritising green infrastructure, such as Berlin (Germany), are also progressive in waste management.

**Air quality (concentration of particulate matter, PM2.5).** We see cities clustered into groups. A few major cities such as Berlin (Germany), Amsterdam (Netherlands), London (UK) and Paris (France) have highly developed infrastructure but moderate air pollution as measured by the concentration of PM2.5 in the air. Scandinavian cities, along with Madrid (Spain), Lisbon (Portugal) and Dublin (Ireland) perform well in terms of air quality. Predominantly Eastern European cities form the group suffering from the poorest air quality.

## Conclusion

From the above analysis of various indicators covering infrastructure, energy, and nature, we see that urban environmental sustainability must be measured in a wider framework to capture a more meaningful indicator of urban environmental sustainability, which, as the [EEA](https://www.eea.europa.eu/themes/sustainability-transitions/urban-environment) suggests, must act as a foundation of future cities. 

For example, London has a high density of certain green infrastructure and performs well in some related measures, but not so well in others. Notably, its efficient public transport system must be coupled with better cyclability and lower congestion. Paris, with its [strong climate-positive policy directions](https://www.timeout.com/paris/en/things-to-do/paris-green-sustainable-city-plan-2030), needs to additionally tackle its low score regarding environmental and ecological quality as part of SDG15.

Of course, every European city is at a different stage on the journey towards fully sustainable development, and each city faces unique challenges in tackling intertwined issues in environmental, social, and economic sustainability. However, we cannot truly laud a city as environmentally sustainable unless it has measured and addressed all components, requiring a shift away from a narrow-scoped model of sustainable urbanisation.

## Appendix

In using the following indicators, we assume that cities are defined in the same way across datasets and that there has been little change between 2019 and 2022.

**[2019 SDG Index and Dashboards Report for European Cities](https://euro-cities.sdgindex.org/)** indicators. We select a few indicators covering SDGs 7, 11, 12, 13 and 15. Further information is available [here](https://s3.amazonaws.com/sustainabledevelopment.report/2019/2019_sdg_index_euro_cities.pdf).

- [SDG15](https://www.globalgoals.org/goals/15-life-on-land/) (life on land), measuring environmental quality:
  - Urban green area (also included separately)
  - Natura 2000 area in good quality
  - Soil sealing
  - Surface water of good ecological status
- Renewable energy generated for SDG7 (affordable and clean energy)
- Air quality metrics: concentration of particulate matter (PM2.5) and emission of nitrogen oxides, as part of SDG11 (sustainable cities)
- Recycling rate and waste quantity, as part of SDG12 (responsible consumption)
- Urban CO2 emissions for SDG13 climate action

**[Clean Cities Campaign 2022 rankings](https://cleancitiescampaign.org/ranking-2022-edition/)** indicators.

- Space for people (opportunity for cycling and pedestrians, congestion)
- Accessibility to climate-friendly mobility - e.g. public transport availability and affordability, EV-charger availability
- Policies score relating to policy pressure on polluting mobility and services offering climate-friendly mobility

Note that individual indicators have limitations. It is difficult to standardise a vast number of metrics, that may be measured differently across the continent, in order to provide a comprehensive analysis. Furthermore, a comprehensive analysis should also study more complex cross-sectoral effects. Future analyses could compare further indicators such as raw energy and water usage and wastage, further per capita measures, risk measures such as flooding risk, and quantification of effects such as the urban heat island effect.