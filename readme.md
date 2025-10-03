[<img src="https://cdn-public.mappls.com/about-mappls/assets/images/mappls-logo.svg" height="60"/> </p>](https://about.mappls.com/api/maps)

## Introduction

Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications.
  

Our APIs, SDKs, and live updating map data available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) give developer-friendly, easy-to-integrate plugins to add capabilities like intelligent
search and routes on map, to your web or mobile applications.

Create your own **Angular/React/Ionic/Cordova Based native app** powered by Mappls Maps and deploy them to various platforms be it **web** or native **mobile** platforms.

### **Package name** : mappls-web-maps

# Sign up for Mappls

Not a mappls user yet? [Sign up](https://apis.mappls.com/console/) for an account here. Once you’re signed in, all you need to start building is a mappls key. You can create and manage your access tokens on your Mappls Account page.

## API Usage

Your MapmyIndia Maps SDK usage needs a set of license keys ([get them here ](https://apis.mappls.com/console/)) and is governed by the API terms and conditions. As part of the terms and conditions, you cannot remove or hide the MapmyIndia logo and copyright information in your project. Please see branding guidelines on MapmyIndia website for more details. The allowed hits are described on the plans page. Note that your usage is shared between platforms, so the API hits you make from a web application, Android app or an iOS app all add up to your allowed daily limit.

## Version History

| Version | Last Updated | Author | Remarks |
| ---- | ---- | ---- | ---- |
| 3.0 | 05 April 2022 | MapmyIndia API Team ([MS](https://github.com/mamtasharma117)) | Initial Commit |
| 3.0 | 02 December 2022 | MapmyIndia API Team ([PK](https://github.com/prabhjot729)) | Document Update |


###   Supported Technologies

- Node.js
- Angular
- React JS
- Cordova
- Ionic

  
### Supported Platforms

- Web
- Android
- iOS

## Getting Started

### Components
- [Map](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md)
	- [Properties ](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#1-properties)
	- [Methods](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#2-map-methods)
	- [Events](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#3--map-events----listening-to-map-events)
	- [Markers](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md)
		- [Adding a marker](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#1--adding-a-marker)
		- [Marker Methods](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#2-marker-methods)
		- [Marker Events](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#3-marker-events)
		- [Adding Multiple Markers](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#iv-adding-multiple-markers)
- [InfoWindows](https://github.com/mappls-api/mappls-web-maps/blob/main/components/infowindow.md)
- [Polylines](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
- [Polygons](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polygons.md)
- [Circle](https://github.com/mappls-api/mappls-web-maps/blob/main/components/circle.md)
- [Overlays](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
	- [Geojson](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
	- [KML](https://github.com/mappls-api/mappls-web-maps/blob/main/components/overlays.md)
	- [Heat Map](https://github.com/mappls-api/mappls-web-maps/blob/main/components/heatmap.md)
### Plugins
- [Place Search](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/placeSearch-plugin)
- [Place Picker](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/placePicker-plugin)
- [Nearby Search](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/nearbySearch-plugin)
- [Directions](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/directions-plugin)
- [getDistance](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/getDistance%20Method)
- [marker-plugin](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/marker-plugin)
- [Eloc-Plugin](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/eLoc-plugin)
- [routeSummary Plugin](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/routeSummary%20Plugin)


## Installation

```js
npm  i  mappls-web-maps
```

### Import Package

- **Angular** : Import mappls class from `mappls-web-maps` package i.e. `app.component.ts` ( or other component of your use case ) .

	```js
	import { mappls, mappls_plugin } from 'mappls-web-maps';
	```
-  **React JS** : Import mappls class from "mappls-web-maps" package inside app.js ( or other component of your use case ).
	```js
	import { mappls, mappls_plugin } from  'mappls-web-maps'
	```

## Implementation

### Loading a Map

-  **Angular / Cordova / Ionic**

```js
import { Component, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';
import { mappls, mappls_plugin } from 'mappls-web-maps';
@Component({
  selector: 'app-root',
  standalone: true,
  imports: [CommonModule],
  template: `
  <div id="map" style="width: 100%; height: 97vh;">
  </div>
`,
})
export class AppComponent implements OnInit {
  mapobject:any
  mapplsClassObject:any= new mappls()
  mapplsPluginObject:any= new mappls_plugin()
  title = 'Map_angular';


  ngOnInit() {
    const loadObject = {
      map: true,
      layer: 'raster', // Optional Default Vector
      version: '3.0', // Optional, other version 3.5 also available with CSP headers
      libraries: ['airspacelayers'], // Optional for Polydraw and airspaceLayers
      plugins: ['direction'], // Optional for any plugins
      //auth:'legacy' /*Use only when you have legacy mappls token*/ 

    };

  this.mapplsClassObject.initialize(
    '---------------Token------------------',
    loadObject,
    () => {
      this.mapobject = this.mapplsClassObject.Map({
        id: 'map',
        properties: {
          center: [28.61, 77.23],
          zoomControl: true,
          location: true,
        },
      });
    }
    
  );
  }
}
```

 -  **React JS**

```js
import { mappls, mappls_plugin } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();
const mapplsPluginObject = new mappls_plugin();


const App = () => {
  const mapRef = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  const loadObject = { 
    map: true, 
    layer: 'raster', // Optional Default Vector
    version: '3.0', // // Optional, other version 3.5 also available with CSP headers
    libraries: ['polydraw'], //Optional for Polydraw and airspaceLayers
    plugins:['direction'] // Optional for All the plugins
};

  useEffect(() => {
    mapplsClassObject.initialize("--------Token-------", loadObject, () => {
      const newMap = mapplsClassObject.Map({
        id: "map",
        properties: {
          center: [28.633, 77.2194],
          zoom: 4,
        },
      });

      newMap.on("load", () => {
        setIsMapLoaded(true);
      });
      mapRef.current = newMap;
    });
    return () => {
      if (mapRef.current) {
        mapRef.current.remove();
      }
    };
  }, []);

  return (
    <div
      id="map"
      style={{ width: "100%", height: "99vh", display: "inline-block" }}
    >
      {isMapLoaded}
    </div>
  );
};

export default App;
```



That’s All !


<br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://www.mapmyindia.com/api/img/icons/support.png)

[Support](https://about.mappls.com/contact/)

Need support? contact us!

<br></br>
<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">&#169; Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
