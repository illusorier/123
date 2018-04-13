Typically D3 requests **vector geographic information** in the form of GeoJSON and **renders this to SVG or Canvas** in the browser.

The 3 concepts that are key to understanding map creation using D3 are:

D3中的地图绘制流程中有三个基本概念：

- GeoJSON (a JSON-based format for specifying geographic data)
- projections (functions that convert from latitude/longitude co-ordinates to x&y co-ordinates)
- geographic path generators (functions that convert GeoJSON shapes into SVG or Canvas paths)

## GeoJSON

GeoJSON is standard for representing geographic data using the JSON format.

        {
          "type": "FeatureCollection",
          "features": [
            {
              "type": "Feature",
              "properties": {
                "name": "Africa"
              },
              "geometry": {
                "type": "Polygon",
                "coordinates": [[[-6, 36], [33, 30], ... , [-6, 36]]]
              }
            },
            {
              "type": "Feature",
              "properties": {
                "name": "Timbuktu"
              },
              "geometry": {
                "type": "Point",
                "coordinates": [-3.0026, 16.7666]
              }
            }
          ]
        }

Each feature consists of **geometry** (simple polygons in the case of countries and a point for Timbuktu) and **properties**.

Properties can contain any information about the feature such as name, id, and other data such as population, GDP etc.

## Projections

A projection function takes a longitude and latitude co-ordinate (in the form of an array `[lon, lat]`) and transforms it into an x and y co-ordinate.

而在Line的生成当中，并不需要这个步骤，因为我们传入的本身就是坐标，而不是经纬度。

Once we have some GeoJSON, a 

The geographic path generator, `d3.geoPath`, is similar to the shape generator in d3-shape: given a GeoJSON geometry or feature object.

Canvas is recommended for dynamic 

`d3.geoPath()`

The given *projection* is typically one of D3's built-in geographic projections;

GeoJSON is 

There are numerous ways of converting (or 'projecting') a point on a sphere (e.g. the earth) to a point on a flat surface (e.g. a screen)

You are free to write your own projection functions but much easier is to ask D3 to make one for you.

To do this, choose a projection method (e.g. `d3.geoEquirectangular`), call it and it will return a projection function.

## Geographic path generators

A geographic path generator is a function that takes a GeoJSON object and convert it into an SVG path string.

In fact, it is just another type of shape generator.

在shape的生成中，我们传入的数组，而在这里，我们传入的是GeoJSON。