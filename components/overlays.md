[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova

# Overlays

  
## Adding a KML Overlay

```js
this.kmlObject = this.mapplsClassObject.KmlLayer({
map:this.mapObject,
url:"https://www.mapmyindia.com/api/advanced-maps/doc/sample/mmi.kml",
cType:0,
fitbounds:true,
fitboundOptions: {padding:  120,duration:1000}
preserveViewport:true
});
```

### Supported Object Types
- Markers
- Polylines
- Polygons


## Adding a Geojson layer

```js
var  mixjson={
"type":  "FeatureCollection",
"features": [
{
"type":  "Feature",
"geometry": {
"type":  "Point",
"coordinates": [ 77.268038, 28.549652, 0 ]
},
"properties": {
"name":  "MapmyIndia1",
"description":  "Okhla delhi",
"styleUrl":  "#mmi_office",
"styleHash":  "-3cca3c32",
"icon":  "1.png",
"stroke":  "#33CC00",
"stroke-opacity":  0.6509803921568628,
"stroke-width":  10,
"fill":  "#FF0000",
"fill-opacity":  0.10196078431372549
}
},
{
"type":  "Feature",
"geometry": {
"type":  "Point",
"coordinates": [ 77.268952, 28.5510446, 0 ]
},
"properties": {
"name":  "MapmyIndia2",
"description":  "68,Okhla delhi",
"styleUrl":  "#mmi_office",
"styleHash":  "-3cca3c32",
"icon":  "1.png",
"stroke":  "#33CC00",
"stroke-opacity":  0.6509803921568628,
"stroke-width":  10,
"fill":  "#FF0000",
"fill-opacity":  0.10196078431372549
}
},
{
"type":  "Feature",
"geometry": {
"type":  "LineString",
"coordinates": [[ 77.268953, 28.551042 ], [ 77.268649, 28.551005 ],
[ 77.268392, 28.550986 ], [ 77.268231, 28.550967 ],
[ 77.268177, 28.550967 ], [ 77.268016, 28.550958 ],
[ 77.267587, 28.55092 ], [ 77.267651, 28.550722 ],
[ 77.267823, 28.55042 ], [ 77.267802, 28.550128 ],
[ 77.267995, 28.549751 ], [ 77.268039, 28.549652 ]]
},
"properties": {
"name":  "Direction1",
"styleUrl":  "#mmi_office",
"styleHash":  "-3cca3c32",
"icon":  "1.png",
"description":  "Direction2",
"stroke":  "#33CC00",
"stroke-opacity":  0.6509803921568628,
"stroke-width":  10,
"fill":  "#FF0000",
"fill-opacity":  1.10196078431372549
}
},
{
"type":  "Feature",
"geometry": {
"type":  "Polygon",
"coordinates": [[ 77.2687822, 28.550868 ],[ 77.268996, 28.550868 ],
[ 77.269039, 28.550383 ], [ 77.268835, 28.550388]]
},
"properties": {
"name":  "MapmyIndia Head Office",
"styleUrl":  "#mmi_area",
"styleHash":  "5617b970",
"stroke":  "#33CC00",
"stroke-opacity":  0.6509803921568628,
"stroke-width":  3,
"fill":  "#33CC00",
"fill-opacity":  0.6509803921568628
}
}]
};
geoJsonObject = this.mapplsClassObject.addGeoJson({
map:this.mapObject,
data:mixjson,
overlap:false,
fitbounds:true,
preserveViewport:true
});
```
  

### Additional Properties for Geojson Markers

  
```js

"icon": "1.png", //for customizing marker
"icon-size":1, // size percentage of the marker: ranging from
"text":"2", // text on marker
"text-size":10, // font size on marker
"text-offset":[0,0], //map anchor offset from the center of icon image.
"text-color":"red"  //color of text on marker
```
  
Email us at [apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com)

![](https://www.mapmyindia.com/api/img/icons/stack-overflow.png)
[Stack Overflow](https://stackoverflow.com/questions/tagged/mapmyindia-api)
Ask a question under the mapmyindia-api

![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

![](https://www.mapmyindia.com/api/img/icons/blog.png)
[Blog](http://www.mapmyindia.com/blog/)
Read about the latest updates & customer stories


> © Copyright 2022 CE Info Systems Ltd. All Rights Reserved. | [Terms & Conditions](http://www.mapmyindia.com/api/terms-&-conditions)