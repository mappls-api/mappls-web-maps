[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Mappls Web Maps - For Angular/ Ionic / Cordova

## Overlays

<p>Overlays refer to the process of combining two or more spatial data layers to create a new layer that retains the information from both original layers. Overlay operations are fundamental in GIS and are used to explore spatial relationships, identify intersections, and derive new information.</p>

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-kml-layer-kfk57l?file=%2Fsrc%2FApp.js%3A1%2C1-60%2C1)
  
## Adding a KML Overlay

#### KML: Keyhole Markup Language is a file format employed to showcase geographical data on maps. With this kml object, you have the capability to superimpose KML data onto Mappls Maps for web applications.
Important Notes to remember
- Only KML data supported.
- KML file must have absolute path or raw KML string (in variable or in textbox)
- All internal URL's path must be absolute. (for icon path etc)
- File must not be password protected.
- File must be CORS enabled from the server where they are hosted.
- File must follow KML standard strictly.

<br>

```js
this.kmlObject = this.mapplsClassObject.KmlLayer({
map:this.mapObject,
url:"https://about.mappls.com/api/advanced-maps/doc/sample/mmi.kml",
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

#### Geojson : GeoJSON overlays refer to the use of GeoJSON data to overlay additional information or features on a map. GeoJSON is a format for encoding geographic data structures, and it is often used to represent features such as points, lines, and polygons along with their properties. When dealing with mapping libraries or platforms that support GeoJSON, you can create overlays to display this geographical information on a map.

<br>

```js
var  mixjson =
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.268038,
                    28.549652,
                    0
                ]
            },
            "properties": {
                "name": "MapmyIndia1",
                "description": "Okhla delhi",
                "styleUrl": "#mmi_office",
                "styleHash": "-3cca3c32",
                "icon": "1.png",
                "stroke": "#33CC00",
                "stroke-opacity": 0.6509803921568628,
                "stroke-width": 10,
                "fill": "#FF0000",
                "fill-opacity": 0.10196078431372549
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.268952,
                    28.5510446,
                    0
                ]
            },
            "properties": {
                "name": "MapmyIndia2",
                "description": "68,Okhla delhi",
                "styleUrl": "#mmi_office",
                "styleHash": "-3cca3c32",
                "icon": "1.png",
                "stroke": "#33CC00",
                "stroke-opacity": 0.6509803921568628,
                "stroke-width": 10,
                "fill": "#FF0000",
                "fill-opacity": 0.10196078431372549
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "LineString",
                "coordinates": [
                    [
                        77.268953,
                        28.551042
                    ],
                    [
                        77.268649,
                        28.551005
                    ],
                    [
                        77.268392,
                        28.550986
                    ],
                    [
                        77.268231,
                        28.550967
                    ],
                    [
                        77.268177,
                        28.550967
                    ],
                    [
                        77.268016,
                        28.550958
                    ],
                    [
                        77.267587,
                        28.55092
                    ],
                    [
                        77.267651,
                        28.550722
                    ],
                    [
                        77.267823,
                        28.55042
                    ],
                    [
                        77.267802,
                        28.550128
                    ],
                    [
                        77.267995,
                        28.549751
                    ],
                    [
                        77.268039,
                        28.549652
                    ]
                ]
            },
            "properties": {
                "name": "Direction1",
                "styleUrl": "#mmi_office",
                "styleHash": "-3cca3c32",
                "icon": "1.png",
                "description": "Direction2",
                "stroke": "#33CC00",
                "stroke-opacity": 0.6509803921568628,
                "stroke-width": 10,
                "fill": "#FF0000",
                "fill-opacity": 1.10196078431372549
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Polygon",
                "coordinates": [
                    [
                        77.2687822,
                        28.550868
                    ],
                    [
                        77.268996,
                        28.550868
                    ],
                    [
                        77.269039,
                        28.550383
                    ],
                    [
                        77.268835,
                        28.550388
                    ]
                ]
            },
            "properties": {
                "name": "MapmyIndia Head Office",
                "styleUrl": "#mmi_area",
                "styleHash": "5617b970",
                "stroke": "#33CC00",
                "stroke-opacity": 0.6509803921568628,
                "stroke-width": 3,
                "fill": "#33CC00",
                "fill-opacity": 0.6509803921568628
            }
        }
    ]
};
geoJsonObject = this.mapplsClassObject.addGeoJson(
    {
        map:this.mapObject,
        data:mixjson,
        overlap:false,
        fitbounds:true,
        preserveViewport:true
    }
);
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

#### **React JS Implementation for kml overlay** : 
```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

const KmlComponent = ({ map }) => {
  const kmlRef = useRef(null);

  useEffect(() => {
    if (kmlRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: kmlRef.current });
    }
    kmlRef.current = mapplsClassObject.KmlLayer({
      map: map,
      url: "https://about.mappls.com/api/advanced-maps/doc/sample/mmi.kml",
      cType: 1,
      fitbounds: true,
      fitboundOptions: { padding: 120, duration: 1000 },
      preserveViewport: true,
    });
  });
};

const App = () => {
  const map = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  useEffect(() => {
    mapplsClassObject.initialize(
      "<Add your Token>",
      { map: true, libraries: ["kml"] },
      () => {
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
      }
    );
  }, []);

  return (
    <div
      id="map"
      style={{ width: "100%", height: "99vh", display: "inline-block" }}
    >
      {isMapLoaded && <KmlComponent map={map.current} />}
    </div>
  );
};
export default App;

```

#### **React JS Implementation for geojson overlays** : 
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
