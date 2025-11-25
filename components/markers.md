[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)
  

# Mappls Web Maps - For Angular/ Ionic / Cordova  

## Markers
  <p>
  Utilizing markers to pinpoint locations is a hassle-free approach. You have the option to use the markers we provide as the default choice, and if you wish to use your own custom markers, we've got that aspect covered as well.
  </p>

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-animated-marker-along-polyline-sf7nyj)

###  1.  Adding a Marker
- **Angular / Cordova / Ionic**
  ```js
  this.markerObject = this.mapplsClassObject.marker({
  map:  this.mapObject,
  position:{lat:28.5512908, lng:77.26809282},
  });
  ```
- **React js**
  ```js
  markerObject = mapplsClassObject.marker({
  map:  mapObject,
  position:{lat:28.5512908, lng:77.26809282},
  });
  ```
- Optional Marker properties
  ```js
  fitbounds:  true, // Set View in which marker's plotted,
  fitboundOptions: 
    { 
      padding:  120, 
      duration:  1000 
    }, //fitbound options
  icon:  'https://apis.mappls.com/map_v3/2.png', // icon url or Path
  width:  25, // marker's icon width
  height:  40, // marker's icon heigh
  clusters:  true, //clusters of marker when zoomed out
  clustersOptions: 
    { 
      "color":  "blue",
      "bgcolor":  "red" 
    },
  offset: [0, 10], // shift marker icon
  popupHtml:  'MapmyIndia', // custom html for marker (<div> content </div>)
  popupOptions: 
    { 
      openPopup:  true, 
      autoClose:  true, 
      maxWidth:  500
    } //popup options
  cType : 0, // 0: for lat,lng combination (Default),1: for the opposite
  });
  ```

### 2. Marker Methods
- Sample Code Snippet
  - **Angular / Cordova / Ionic**
    ```js
    this.markerObject.setPosition({lat:28.454,lng:77.5454});
    this.markerObject.setIcon("https://apis.mappls.com/map_v3/1.png");
    ```
  - **React js**
    ```js
    markerObject.setPosition({lat:28.454,lng:77.5454});
    markerObject.setIcon("https://apis.mappls.com/map_v3/1.png");
    ```
-  `setIcon`: Setting the URL of the icon. It replaces the icon URL.
-  `setDraggable`: To make the marker draggable.
-  `setPosition`: Setting the Position of the marker.
-  `setZIndex`: Setting the priority index of the marker.
-  `setPopup`: Setting Popup
-  `getPosition`: Returns the compass heading of aerial imagery.
### 3. Marker Events
- Sample Code Snippet
  - **Angular / Cordova / Ionic**
    ```js
    this.markerObject.addListener('load', function () { console.log('load');});
    ```
  - **React js**
    ```js
    markerObject.addListener('load', function () { console.log('load');});
    ```
-  `click`: Fired when a pointing device (usually a mouse) is pressed on the marker.
-  `cursor_changed`: Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
-  `dblclick`: Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  `drag`: Fired repeatedly during a "drag to pan" interaction.
-  `dragstart`: Fired when a "drag to pan" interaction starts.
-  `dragend`: Fired when a "drag to pan" interaction ends.
-  `draggable_changed`: This event is fired when the marker's draggable property changes.
-  `mousedown`: This event is fired for a mousedown on the marker.
-  `mouseout`: This event is fired when the mouse leaves the area of the marker icon..
-  `mouseover`: This event is fired when the mouse enters the area of the marker icon.
-  `mouseup`: This event is fired for a mouseup on the marker.  

### IV. Adding Multiple Markers

####    a) Multiple Markers as Cluster

Example :  Angular *// Refer below code  without `this.` for **React js** reference.*
```js
var  geoData=
{
  "type":  "FeatureCollection",
  "features": [
    {
      "type":  "Feature",
      "properties": 
        {
          "htmlPopup":"noida"
        },
      "geometry": 
        {
          "type":  "Point",
          "coordinates": [28.544,77.5454]
        }
    },
    {
      "type":  "Feature",
      "properties": 
        {
          "htmlPopup":"faridabad"
        },
      "geometry": 
        {
          "type":  "Point",
          "coordinates": [28.27189158,77.2158203125]
        }
    },
    {
      "type":  "Feature",
      "properties": 
        {
          "htmlPopup":"delhi"
        },
      "geometry": 
        {
          "type":  "Point",
          "coordinates": [28.549511,77.2678250]
        }
    }
  ]
};

this.markerObject = this.mapplsClassObject.marker(
  {
    map:this.mapObject,
    position:geoData,
    icon:'https://apis.mappls.com/map_v3/1.png',
    clusters:true,
    fitbounds:true,
    fitboundOptions:
      {
        padding:  120,
        duration:1000
      },
    popupOptions:
      {
        offset: {'bottom': [0, -20]}
      }
  }
); 
```

#### b) Multiple Markers as Geojson
 Example :  **Angular / Cordova / Ionic** *// Refer below code  without `this.` for **React js** reference.*

```js
var  geoData=
{
  "type":  "FeatureCollection",
  "features": 
    [
      {
        "type":  "Feature",
        "properties":
          {
            "description":"noida",
            "icon":"https://apis.mappls.com/map_v3/1.png",
            "icon-size":.75,
            "icon-offset":[0,-10],
            "text":"1",
            "text-size":10,
            "text-offset":[0,.6]
          },
        "geometry": 
          {
            "type":  "Point",
            "coordinates": [28.544,77.5454]
          }
      },
      {
        "type":  "Feature",
        "properties": 
          {
            "description":"faridabad",
            "icon":"https://apis.mappls.com/map_v3/1.png"
          },
        "geometry": 
          {
            "type":  "Point",
            "coordinates": [28.27189158,77.2158203125]
          }
      },
      {
        "type":  "Feature",
        "properties": 
          {
            "description":"delhi",
            "icon":"https://apis.mappls.com/map_v3/1.png"
          },
        "geometry": 
          {
            "type":  "Point",
            "coordinates": [28.549511,77.2678250]
          }
      }
    ]
};
var  this.markerObject=this.mapplsClassObject.addGeoJson(
  {
    map:this.mapObject,
    data:geoData,
    fitbounds:true,
    cType:0
  }
);
```

**React JS Implementation**
```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

var pts = [
  { lat: 28.55108, lng: 77.26913 },
  { lat: 28.55106, lng: 77.26906 },
  { lat: 28.55105, lng: 77.26897 },
  { lat: 28.55101, lng: 77.26872 },
  { lat: 28.55099, lng: 77.26849 },
  { lat: 28.55097, lng: 77.26831 },
  { lat: 28.55093, lng: 77.26794 },
  { lat: 28.55089, lng: 77.2676 },
  { lat: 28.55123, lng: 77.26756 },
  { lat: 28.55145, lng: 77.26758 },
  { lat: 28.55168, lng: 77.26758 },
  { lat: 28.55175, lng: 77.26759 },
  { lat: 28.55177, lng: 77.26755 },
  { lat: 28.55179, lng: 77.26753 },
];

const PolylineComponent = ({ map }) => {
  const polylineRef = useRef(null);

  useEffect(() => {
    if (polylineRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: polylineRef.current });
    }
    polylineRef.current = mapplsClassObject.Polyline({
      map: map,
      paths: pts,
      strokeColor: "red",
      strokeOpacity: 1.0,
      strokeWeight: 10,
      fitbounds: true,
      animate: {
        speed: 5,
        icon_width: 25, // or as “25”
        icon_height: 50, // or as “50”,
        icon_url:
          "http://about.mappls.com/api/advanced-maps/doc/sample/map_sdk/car.png", //Place your icon url
        repeat: false, //false,
      },
    });
  });
};

const App = () => {
  const map = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  useEffect(() => {
    mapplsClassObject.initialize("Add your Token", { map: true }, () => {
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
      {isMapLoaded && <PolylineComponent map={map.current} />}
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
