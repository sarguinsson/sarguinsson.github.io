---
title: "Beer mapping with python (Part 1)"
date: 2022-01-02 16:08:41 +0100
categories: GIS
tags:
  - Cartography
  - Maps
  - Python
toc: true
---

Recently, there was a discusion into my close circle of friends about beer price in our hometown Girona. So I decided to start a little research on this topic, to bring strong arguments into next meeting and taking advantadge on my software skills. I decided to get into map data visualization. In this article we will walk through diferent kinds of datasets to display bar locations and zones with higher rate of bars.

## Datasets

Before starting to draw maps, I'll explain the used datasets for this blog entry. The datasets url are specified in references part.

To get all the bars I used "activitats2020_bars.csv" which is a filtered csv with all the activities that rerference a Bar in Girona.

- Activities file (.csv)

Also whith friends we are feeding an Mongo DB with bars and prices

For neighbourhood shapes it's being used:

- Neigbourhoods shapes zip file --> that includes

  - .shp
  - .dbf
  - .sbn
  - .sbx
  - .shp.xml
  - .shx

## Display bar locations with points

```python
import folium
import pandas as pd
import pymongo

input_nbh_shp = "./Barris.shp"
input_activities = "./activities2020_bars.csv"

nbh_sbh_df = gpd.read_file(input_nbh_shp)
act_df = gpd.read_file(input_activities)

nbh_sbh_df = nbh_sbh_df.to_crs(epsg=4236)

center = [41.97969558739158, 2.8213967358161915]
```

<img src='{{ site.url }}/images/posts/add_points_to_map_00.png'>

<img src='{{ site.url }}/images/posts/add_points_to_map_01.png'>

## Display bar locations with clusters

Some text

Some Code

Some Image

## Display neighbourhoods with bar sum

```python
import folium
import pandas as pd
import pymongo

input_nbh_shp = "./Barris.shp"
input_activities = "./activities2020_bars.csv"

nbh_sbh_df = gpd.read_file(input_nbh_shp)
act_df = gpd.read_file(input_activities)

nbh_sbh_df = nbh_sbh_df.to_crs(epsg=4236)

center = [41.97969558739158, 2.8213967358161915]
```

<img src='{{ site.url }}/images/posts/add_nbh_shapes_to_map_00.png'>

## References

- Zheng, J. (2019, November 08). jingwen-z.github.io. Retrieved from jingwen-z.github.io: [How to draw a variety of maps with folium in python?][how-to-draw-a-variety-of-maps-with-folium-in-python?]
- Girona.cat. 2022. Establiments dedicats a activitats econòmiques - Activitats2020.csv - Girona Open Data. [online] Available at: [Girona Open Data - activities][ajuntament-de-girona-open-data-activities]
- Girona.cat. 2022. Barris - Barris.zip - Girona Open Data. [online] Available at: [Girona Open Data - neighbourhoods][ajuntament-de-girona-open-data-neighbouhoods]

[how-to-draw-a-variety-of-maps-with-folium-in-python?]: https://jingwen-z.github.io/how-to-draw-a-variety-of-maps-with-folium-in-python/
[ajuntament-de-girona-open-data-activities]: https://terra.girona.cat/opendata/storage/f/2021-02-01T09%3A55%3A29.147Z/activitats2020.csv
[ajuntament-de-girona-open-data-neighbouhoods]: https://www.girona.cat/opendata/dataset/barris/resource/eaae36f4-4013-4718-ab4a-7daecdb6ddad
