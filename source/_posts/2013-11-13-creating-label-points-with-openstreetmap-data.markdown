---
layout: post
title: "Creating Label Points With OpenStreetMap Data"
date: 2013-11-13 19:13
comments: true
keywords: "linux, gis, open source, PostGIS, OpenStreetMap, labels"
categories: 
- PostGIS
- OpenStreetMap
---
## tl;dr

``` sql
SELECT name, ST_Area(Geography(ST_Transform((ST_DUMP(ST_BUFFER(ST_Collect(geometry), 0))).geom,4326))) AS area, ST_PointOnSurface((ST_DUMP(ST_BUFFER(ST_Collect(geometry), 0))).geom) AS geom
FROM osm_new_waterareas
WHERE name IS NOT NULL
GROUP BY name
```
<!-- more -->

## Overview

[OpenStreetMap](http://www.openstreetmap.org/) is one the most amazing data projects I know of.
The breadth of high-quality, high-precision features contained with the OSM Planet never ceases
to amaze me. That being said, the freedom of the OSM data model, which allows this high-level of
flexibility and openness, is not without its problems. One of the major problems I've run into
recently have been the generation of label points derived from Open Street Map.

The following example is illustrative of the primary problem faced when generating label points,
overlapping geometries. The SQL statement below returns all features with an [imposm](http://imposm.org)
database's `osm_new_waterareas` table named, 'Lake Chelan'. Three geometries are returned, one
representing the entire lake, and two others representing northern and southern sections of the lake.
All three share a name of, 'Lake Chelan', but two are of type `water`, and one is of type `reservoir`.

``` sql
SELECT name, type, osm_id
FROM osm_new_waterareas
WHERE name = 'Lake Chelan';

    name     |   type    |  osm_id   
-------------+-----------+-----------
 Lake Chelan | reservoir |    446718
 Lake Chelan | water     | 135297050
 Lake Chelan | water     |  52045429
```

Click the map below to view each of the three geometries.

{% gist 03d7f78a1591971ed2d8 chelan.geojson %}

Rendering label points using PostGIS's [ST_PointOnSurface()](http://postgis.org/docs/ST_PointOnSurface.html) 
function would yield three separate points, as illustrated below. I however, would like only a single
label point for each feature.

{% gist 9cf8b49844cb43dfae81 chelan.geojson %}

In addition to a single label point, I'd also like to attribute that label point with an area value, to be used
as a toggle for display at varying zoom levels.