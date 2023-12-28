[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)

# getDistance Method for Mappls Web Maps

**Easy To Integrate Distance Matrix APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Distance Method.


## Document Version History

| Version | Remarks | Author |
| ---- | ---- | ---- |
| 3.0 | Document Added | Mappls API Team ([MS](https://github.com/mamtasharma117)) |
| 3.0 | Document Update |SDK Product Team ([PK](https://github.com/prabhjot729/))|


## Introduction

This method, offered by Mappls web plugins , computes the routable distance and duration between a set of source/primary positions and a list of all supplied secondary positions using two mode of route calculation i.e. optimal OR shortest. The method also takes into account different modes of transport like 4 wheelers, two wheelers + more. Please note that maximum number of points are limited to 100 only including source and secondary positions.

The method offers the following basic functionalities: 
1. The method computes the distance and duration from origin to number of supplied destinations on maps.
2. The ability to set the vehicle profile like driving, biking and trucking.
3. Easily set the resource for traffic and ETA information.
4. The method also has 'many to many' functionality in case of multiple origins and destinations.
5. It allows to use origin and destinations in Mappls's digital address (semicolon separated) eLoc or WGS 84 geographical coordinates both.
6. This method can only be used when **`CORS`** is enabled on your project. For details, please contact apisupport@mappls.com.

For detailed understanding, Let’s get started!

## Live Demo

Web sdk implementation : [Mappls Live Demo](https://about.mappls.com/api/web-sdk/vector-plugin-example/Distance/mappls-default-getdistance-plugin)

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-getdistance-plugin-j2swrq?file=%2Fsrc%2FApp.js%3A1%2C1-78%2C1)



## Implementation
## React JS
```js
import { mappls, mappls_plugin } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();
const mapplsPluginObject = new mappls_plugin();

const GetdistancePlugin = ({ map }) => {
  const getDistanceRef = useRef(null);

  useEffect(() => {
    if (map && getDistanceRef.current) {
      getDistanceRef.current.remove();
      mapplsClassObject.removeLayer({ map, layer: getDistanceRef.current });
    }

    getDistanceRef.current = mapplsPluginObject.getDistance(
      {
        map: map,
        coordinates: "mmi000;123zrr",
        eloc: ["mmi000", "123zrr"],
        popupHtml: ["<h1>MMI</h1>”,”<h1>Agra</h1>"],
        html: ["1", "2"],
        icon: { url: "2.png", width: 30, height: 45 },
      },
      callback_method
    );
    function callback_method(data) {
      console.log(data);
    }
    return () => {
      if (map && getDistanceRef.current) {
        mapplsClassObject.removeLayer({ map, layer: getDistanceRef.current });
      }
    };
  }, [map]);
};

const App = () => {
  const mapRef = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  const loadObject = { map: true, plugins: ["getDistance"] };

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
      {isMapLoaded && <GetdistancePlugin map={mapRef.current} />}
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
  template:
    '<div  id="map"  style="width: 99%; height: 99vh; background-color: white;"></div>',
  styleUrls: ['./app.component.css'],
})
export class AppComponent implements OnInit {
  mapObject: any;
  mapplsClassObject = new mappls();
  mapplsPluginObject = new mappls_plugin();

  mapProps = {
    center: [28.633, 77.2194],
    traffic: false,
    zoom: 4,
    clickableIcons: false,
  };

  ngOnInit() {
    const loadObject = {
      map: true,
      plugins: ['getDistance'],
    };

    this.mapplsClassObject.initialize(
      '<----- Add your token here ------>',
      loadObject,
      () => {
          this.mapplsPluginObject.getDistance(
            {
              map: this.mapObject,
              coordinates: 'mmi000;123zrr',
              eloc: ['mmi000', '123zrr'],
              popupHtml: ['<h1>MMI</h1>”,”<h1>Agra</h1>'],
              html: ['1', '2'],
              icon: { url: '2.png', width: 30, height: 45 },
            },
            callback_method
          );
          function callback_method(data: any) {
            console.log(data);
          }
      });
  }
}
```


## Properties

### Mandatory

1. `coordinates` (string): Semicolon separated eloc or lat,long or both.
2. `callback`: Method to get response
### Optional
1. `resource` (string): Default is `distance_matrix` and can be changed to `distance_matrix_eta` or `distance_matrix_traffic` as per requirement.
2. `profile` (string): Default `driving` for four wheelers and can be changed to `biking` and `trucking` for two wheelers and heavy vehicles respectively.
3. `rtype` (boolean): type of route required for navigation, where values mean:
    -   `0` optimal (default) 
    -   `1` shortest (it will calculate route by excluding access penalties like private roads, etc.)

4. `region` (string): It is for the available countries. Default is India; for other countries (Sri Lanka, Nepal, Bangladesh & Bhutan) this parameter is mandatory. Possible values are `ind` (for India, default), `lka` (for Sri Lanka) , `npl` (for Nepal) , `bgd` (for Bangladesh), `mmr` (for Myanmar) and `btn` (for Bhutan).

5. `sources` (string): To specify which of the coordinates/eLoc supplied are to be treated as *source* position for 'many to many' distance matrix calculation. The input is indicative of that coordinate/eLoc's index.
E.g. 0;1 means that 0th and 1st pairs are source points. Default value is 0. The indexes must be semi-colon separated. e.g: 0;1;2;...
6. `destinations` (string): To specify which of the coordinates/eLoc supplied in the method are to be treated as destination position for 'many to many' distance matrix calculation. The input is indicative of that coordinate/eLoc's index. 
E.g. 2;3 means that 0th and 1st pairs are destination points. Default value is all. The indexes must be comma separated. e.g: 3;4;5;...


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




<div align="center">&#169 Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
