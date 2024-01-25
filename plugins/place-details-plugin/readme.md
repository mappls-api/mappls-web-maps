[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Place Details Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls PIN (eLoc) Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placedetails/mappls-placedetails-plugin) 


## Document Version History

| Version | Remarks | Author |
| ---- | ---- | ---- |
| 3.0 | Document Added | Mappls API Team ([MS](https://github.com/mamtasharma117)) |
| 3.0 | Document Update |SDK Product Team ([PK](https://github.com/prabhjot729/))|



## Introduction

A simple plugin / widget to render details of a particular place. The Place Details plugin for MapmyIndia Web Map JS library is provided as a means to enable rendering of MapmyIndia Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web map implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to render places directly on map with reference to the provided eLoc(s).
2. A getPinDetails() method to fetch the details of a place.
3. Customizable markers
4. Remove markers from map.

## Live Demo

Visit the following link for visiting the live demo:

Web sdk implementation [Mappls Live Demo](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin)

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-getpindetails-plugin-39qrlc?file=%2Fsrc%2FApp.js%3A1%2C1-70%2C1)

For detailed understanding, Let’s get started!

## Add the Place Details plugin
### Implementation

## React JS


```js
import { mappls, mappls_plugin } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();
const mapplsPluginObject = new mappls_plugin();

const PlacedetailsPlugin = ({ map }) => {
  const placedetailsRef = useRef(null);

  useEffect(() => {
    if (map && placedetailsRef.current) {
      placedetailsRef.current.remove();
      mapplsClassObject.removeLayer({ map, layer: placedetailsRef.current });
    }

    placedetailsRef.current = mapplsPluginObject.getPinDetails(
      { pin: "mmi000" },
      (e) => {
        console.log(e); /* get details in console */
      }
    );
    return () => {
      if (map && placedetailsRef.current) {
        mapplsClassObject.removeLayer({ map, layer: placedetailsRef.current });
      }
    };
  }, [map]);
};

const App = () => {
  const mapRef = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  const loadObject = { map: true, plugins: ["placedetails"] };

  useEffect(() => {
    mapplsClassObject.initialize("<Add your Token>", loadObject, () => {
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
      {isMapLoaded && <PlacedetailsPlugin map={mapRef.current} />}
    </div>
  );
};

export default App;
```
## Angular
```js
import { Component, OnInit } from '@angular/core';
  import { mappls, mappls_plugin } from 'mappls-web-maps';
  
  @Component({
    selector: 'app-root',
    template:'',
    styleUrls: ['./app.component.css'],
  })
  export class AppComponent implements OnInit {
    mapplsClassObject = new mappls();
    mapplsPluginObject = new mappls_plugin();
  
  
    ngOnInit() {
      const loadObject = {
        map: false,
        plugins: ['getPinDetails'],
      };
  
      this.mapplsClassObject.initialize(
        '<----- Add your token here ------>',
        loadObject,
        () => {
  
            var elocObj = this.mapplsPluginObject.getPinDetails(
              { pin: 'mmi000' },
              (e: any) => {
                console.log(e);
              }
            );
  
        }
      );
    }
  }

```

#### Mandatory Parameters
1. `pin`: The pin (Mappls Pin/Eloc) whose details are required.
2. `callback`: to return data to a specified callback method.


#### Optional Parameters
1. `map`: Map Object
2. `icon`: custom icon url.
3. `divId`: The div to put the result in.
4. `markerPopup` (boolean): to show pop-ups on marker click. Default is true.(example: `markerPopup:true`)
5. `popupHtml`: to show html pop up on marker click. User should define values to be shown while using this parameter.(example: `obj.setPopup({content:"<h1>Hello MapmyIndia</h1>"})`)
6. `fitbounds` (boolean): To show all rendered eLoc(s) in a single view bound. (example: `fitbounds:true`)
7. `fitboundOptions` : padding in fitbounds, if any. (Example: `{ padding:50,maxZoom:18}`)
8. `infoDiv` (boolean): To render html div on map or not. Default is true. (example: `infoDiv:true`)
9. `click_callback`: method to call on click of callback. 

### 3. Method to remove the markers with callback populated by Place Details Plugin

```js
getPinDetailsObj.remove();
```

### 4. Method to set up the div content for populating details from getPinDetails() plugin

```js
getPinDetailsObj.setDivContent(“Div html);
```
### 5. Method to set up the pop up content on marker as html.
For Eg:

```js
getPinDetailsObj.setPopup({content:"<h1>Hello Mappls</h1>"});
```


That's All ! 

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




<div align="center">&copy Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
