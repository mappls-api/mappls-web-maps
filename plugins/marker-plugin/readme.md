[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Marker Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Marker Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Marker/mappls-marker-plugin) 


## Document Version History

| Version | Remarks | Author |
| ---- | ---- | ---- |
| 3.0 | Document Added | Mappls API Team ([MS](https://github.com/mamtasharma117)) |
| 3.0 | Document Update |SDK Product Team ([PK](https://github.com/prabhjot729/))|



## Introduction

A simple plugin to render places on map as markers. The Marker plugin for Mappls Web Maps JS library is provided as a means to enable rendering of searched Places via eLoc as markers top of Mappls Maps. 

The plugin can be used in combination with our Interactive Map JS libraries.

The SDK offers the following basic functionalities: 
1. Ability to render places directly using eLoc on Mappls Maps SDK.
2. A Mappls.elocMarker() method to initiate rendering of Places on the map specified with eLoc(s) on the map.
3. Ability to add listeners on marker events, remove markers, customize icons and get fitbounds of the markers. 
4. Ability to make markers draggable and add annotations (info popups + customizable popups).


## Live Demo

Visit the following link for visiting the live demo:

Web sdk implementation : [Mappls Live Demo](https://about.mappls.com/api/web-sdk/vector-plugin-example/Marker/mappls-marker-plugin)

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-pinmarker-plugin-vzcd59?file=%2Fsrc%2FApp.js)



## Add the Marker plugin
### Implementation

## React JS
```js
import { mappls, mappls_plugin } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();
const mapplsPluginObject = new mappls_plugin();

const PinmarkerPlugin = ({ map }) => {
  const pinMarkerRef = useRef(null);

  useEffect(() => {
    if (map && pinMarkerRef.current) {
      pinMarkerRef.current.remove();
      mapplsClassObject.removeLayer({ map, layer: pinMarkerRef.current });
    }

    pinMarkerRef.current = mapplsPluginObject.pinMarker(
      {
        map: map,
        pin: "mmi000",
        popupHtml: '<h1 style="color:green">MapmyIndia</h1>',
      },
      (e) => {
        console.log(e);
      }
    );
    return () => {
      if (map && pinMarkerRef.current) {
        mapplsClassObject.removeLayer({ map, layer: pinMarkerRef.current });
      }
    };
  }, [map]);
};

const App = () => {
  const mapRef = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  const loadObject = { map: true, plugins: ["pinMarker"] };

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
      {isMapLoaded && <PinmarkerPlugin map={mapRef.current} />}
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
  template: `<div
    id="map"
    style="width: 99%; height: 99vh; background-color: white;"
  ></div>`,
  styleUrls: ['./app.component.css'],
})
export class AppComponent implements OnInit {
  mapObject: any;
  marker: any;
  mapplsClassObject = new mappls();
  mapplsPluginObject = new mappls_plugin();

  mapProps = {
    center: [28.633, 77.2194],
    traffic: false,
    zoom: 4,
    geolocation: false,
    clickableIcons: false,
  };

  ngOnInit() {
    const loadObject = {
      map: true,
      plugins: ['pinMarker'],
    };

    this.mapplsClassObject.initialize(
      '<----- Add your token here ------>',
      loadObject,
      () => {
        this.mapObject = this.mapplsClassObject.Map({
          id: 'map',
          properties: this.mapProps,
        });

        this.mapObject.on('load', () => {
          var obj = this.mapplsPluginObject.pinMarker(
            {
              map: this.mapObject,
              pin: 'mmi000',
              popupHtml: '<h1 style="color:green">MapmyIndia</h1>',
            },
            (e: any) => {
              console.log(e);
            }
          );
        });
      }
      );
    }
  }
 ```

#### Mandatory Parameters
1. `map`: object > vector map or raster map object from respective Mappls Map JS.
2. `pin`: array of strings containing the eLoc(s) which need to be showcased on the map. <br> e.g. 
    ```html
    [‘mmi000’,’123zrrr’]
    ```

#### Optional Parameters
1. `html`: (string or html) Text which needs to be written over the marker or if there is a need for further customization, then this param can also take in HTML div. <br>
e.g. 
    ```html
    'mappls'
    ```
    OR 
    ```
    [“<b>MMI</b>”,”<b>AGRA</b>”]
    ```
2. `popupHtml`: (string or HTML) What needs to be displayed when marker is clicked. <br>e.g. 
    ```
    [“<h1>Mappls</h1>”,”<p>Agra</p>”]
    ```
3. `popupOptions`: (object) if the popup/annotation needs to be customized further. 
The following are the sub-params for the object: 
    - `className`: the class name of the annotation object.
    - `offset`: the offset positioning from the marker.
    - `openPopup`: (boolean) indicating if the pop needs to be open on addition of marker or not as default.
    <br> e.g. 
    ```js
    {
        className:'myClass',
        offset:{},
        openPopup:true //open popup as default with add marker
     }
    ```
4. `icon`: (object) the customized marker icon options. The following are the sub-params for the object: 
    - `url`: the URL specifying the marker image.
    - `width`: width of the marker icon.
    - `height`: height of the marker icon.
    - `offset`: offset positioning of the marker's anchor.
    - `popupAnchor`: positioning of the marker popup's anchor.
    <br>
    
    e.g. 
    ```js
    {
        url:'https://apis.mappls.com/map_v3/2.png',
        width:30,
        height:40,
        offset:[20,40],
        popupAnchor:[-5,-40]
    }
    ```
5. `draggable`: (boolean) to set the marker(s) as draggable or not.    

<br>

### 2. Method for getting all markers to fit in a viewbound
#### Method
`fitbounds()`

```js
pinMarkerObj.fitbounds(options); //options are optional e.g. {padding:100}
```

- `padding`: option can be used to setup a padding around the viewbound to fit the markers in.

### 3. Method for removing markers with callback
#### Method
`remove()`

```js
pinMarkerObj.remove();
```

### 4. Method for adding event listeners on the marker
#### Method
`addListener()`

```js
pinMarkerObj.addListener(event,callback);
```

Example: 
```js
pinMarkerObj.addListener(‘click’,function(data){console.log(data);});
```

### 5. Method for removing event listeners on the marker
#### Method
`removeListener()`

```js
pinMarkerObj.removeListener(event);
```

Example: 
```js
pinMarkerObj.removeListener(‘click’);
```

### 6. Method for setting icons for markers
#### Method
`setIcon()`

```js
pinMarkerObj.setIcon(‘url.png’); //replaces all marker's icon.
```

OR

```js
pinMarkerObj.setIcon(‘url.png’,’mmi000’); //replaces single marker's icon for the provided eLoc.

```

### 7. Method for setting popuphtml for markers
#### Method
`setPopup()`

```js
pinMarkerObj.setPopup({content:"<h1>Mappls</h1>"}); //replaces all marker's pop up values.
```

OR

```js
pinMarkerObj.setPopup({content:"<h1>Agra</h1>",pin:'123zrr'}); //replaces single marker's popup value for the provided Pin.
```

<br>


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




<div align="center">&copy  Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
