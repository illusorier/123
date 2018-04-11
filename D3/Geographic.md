GeoJSON is standard for representing geographic data using the JSON format.

A projection function takes a longitude and latitude co-ordinate (in the form of an array `[lon, lat]`) and transforms it into an x and y co-ordinate.

而在Line的生成当中，并不需要这个步骤，因为我们传入的本身就是坐标，而不是经纬度。

A geographic path generator is a function that takes a GeoJSON object and convert it into an SVG path string.

In fact, it is just another type of shape generator.

在shape的生成中，我们传入的数组，而在这里，我们传入的是GeoJSON。

Once we have some GeoJSON, a 

`d3.geoPath()`

The given *projection* is typically one of D3's built-in geographic projections;