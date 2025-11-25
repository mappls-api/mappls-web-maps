[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)

# Mappls Web Maps - For Angular/ Ionic / Cordova

## Polygon

<p>Polygons are a way of showing a territory. In cases where you want to showcase data over an area, polygons are your best pick. You can use them to show Geozones as well.

It’s very like generating a polyline, the basic steps remain the same, create a Data set, generate a polygon and add it to the map.</p>

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-geojson-layer-nw9ddv?file=%2Fsrc%2FApp.js%3A1%2C1-142%2C1)  

### 1. Adding a Polygon

```js
this.polygonObject = this.mapplsClassObject.Polygon(
{
	map:this.mapObject,
	paths: [ 
		{
			"lng":"77.26872","
			lat":  "28.55101"
		},
		{
			"lng":"77.26849",
			"lat":"28.55099"
		},
		{
			"lng":"77.26831",
			"lat":"28.55097"
		},
		{
			"lng":"77.26794",
			"lat":"28.55093"
		},
		{
			"lng":"77.2676",
			"lat":"28.55089"
		},
		{
			"lng":"77.26756",
			"lat":"28.55123"
		},
		{
			"lng":"77.26758",
			"lat":"28.55145"
		},
		{
			"lng":"77.26758",
			"lat":"28.55168"
		},
		{
			"lng":"77.26759",
			"lat":"28.55172"
		}
	],
});
```
- Optional  Polygon properties

```js
fillColor:  "red",
fillOpacity:  0.3,
strokeColor:  "red",
strokeOpacity:  0.8,
html:"MMI",
fitbounds:  true,
fitboundOptions: 
	{
		padding: 120,
		duration:1000
	},
popupHtml: 'Route 1',
popupOptions: 
	{
		offset: 
			{
				'bottom': [0, -20]
			}
	},
center:
	{
		{ 
			"lat":  "17.355529", 
			"lng":  "78.493919"
		}
	}
```

  

### 2.  Polygon Events
-  `click`: Fired when a pointing device (usually a mouse) is pressed on the marker.

	Example :  Angular / Cordova / Ionic <br>
	Refer below code  without `this.` for React js reference.
	```js
	polygonObject.addListener('load', function () { console.log('click');});
	```
-  `dblclick`: Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  `drag`: Fired repeatedly during a "drag to pan" interaction.
-  `dragstart`: Fired when a "drag to pan" interaction starts.
-  `dragend`: Fired when a "drag to pan" interaction ends.
-  `draggable_changed`: This event is fired when the marker's draggable property changes..
-  `mousemove`: Fired when mouse move.
-  `mouseover`: This event is fired when the mouse enters the area of the marker icon.


### Remove Polygon

```js
mapplsClassObject.removeLayer({
  map: mapObject,
  layer: polygonObject,
});
```

**React Js Implementation for Polygon**
```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

var mixjson = {
  type: "FeatureCollection",
  features: [
    {
      type: "Feature",
      geometry: {
        type: "Point",
        coordinates: [28.5495, 77.267854],
      },
      properties: {
        name: "MapmyIndia old Office",
        description: "Okhla delhi",
        icon: "https://apis.mappls.com/map_v3/1.png",
        "icon-size": 1,
        text: "",
        "text-size": 20,
        "text-offset": [0, 0],
        "text-color": "red",
      },
    },
    {
      type: "Feature",
      geometry: {
        type: "Point",
        coordinates: [28.5510446, 77.268952],
      },
      properties: {
        name: '<div onclick="function1()">MapmyIndia New Office</div>',
        description: "68,Okhla delhi",
        icon: "https://apis.mappls.com/map_v3/1.png",
        "icon-size": 0.55,
        text: "1",
        "icon-offset": [0, -20],
      },
    },
    {
      type: "Feature",
      geometry: {
        type: "LineString",
        coordinates: [
          [28.551042, 77.268953],
          [28.551005, 77.268649],
          [28.550986, 77.268392],
          [28.550967, 77.268231],
          [28.550967, 77.268177],
          [28.550958, 77.268016],
          [28.55092, 77.267587],
          [28.550722, 77.267651],
          [28.55042, 77.267823],
          [28.550128, 77.267802],
          [28.549751, 77.267995],
          [28.549652, 77.268039],
        ],
      },
      properties: {
        name: "Direction1",
        description: "Direction2",
        stroke: "#33CC00",
        "stroke-opacity": 0.6509803921568628,
        "stroke-width": 10,
      },
    },
    {
      type: "Feature",
      geometry: {
        type: "Polygon",
        coordinates: [
          [
            [28.550868798522835, 77.26878225803375],
            [28.550868798522835, 77.26899683475493],
            [28.550383454405356, 77.26903975009918],
            [28.550388166494926, 77.26883590221404],
          ],
        ],
      },
      properties: {
        name: "MapmyIndia Head Office",
        stroke: "#33CC00",
        "stroke-opacity": 0.6509803921568628,
        "stroke-width": 3,
        fill: "#33CC00",
        "fill-opacity": 0.6509803921568628,
      },
    },
  ],
};

const GeoJsonComponent = ({ map }) => {
  const geoJsonRef = useRef(null);

  useEffect(() => {
    if (geoJsonRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: geoJsonRef.current });
    }
    geoJsonRef.current = mapplsClassObject.addGeoJson({
      map: map,
      data: mixjson,
      overlap: false,
      fitbounds: true,
      preserveViewport: true,
    });
  });
};

const App = () => {
  const map = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  useEffect(() => {
    mapplsClassObject.initialize("<Add your Token>", { map: true }, () => {
      if (map.current) {
        map.current.remove();
      }
      map.current = mapplsClassObject.Map({
        id: "map",
        properties: {
          center: [28.633, 77.2194],
          zoom: 4,
        },
      });
      map.current.on("load", () => {
        setIsMapLoaded(true);
      });
    });
  }, []);

  return (
    <div
      id="map"
      style={{ width: "100%", height: "99vh", display: "inline-block" }}
    >
      {isMapLoaded && <GeoJsonComponent map={map.current} />}
    </div>
  );
};
export default App;
```




<br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://about.mappls.com/api/img/icons/support.png)
[Support](https://about.mappls.com/contact/)
Need support? contact us!

<br></br>
<br></br>

[<p align="center"> <img src="https://about.mappls.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://about.mappls.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://about.mappls.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://about.mappls.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://about.mappls.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://about.mappls.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://about.mappls.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
