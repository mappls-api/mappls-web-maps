[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Place Search Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Place Search Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placesearch/mappls-placesearch-plugin)

## Document Version History

| Version | Remarks | Author |
| ---- | ---- | ---- |
| 3.0 | Document Added | Mappls API Team ([MS](https://github.com/mamtasharma117)) |
| 3.0 | Document Update |SDK Product Team ([PK](https://github.com/prabhjot729/))|


## Introduction

A simple plugin / widget to search for places powered by the best online maps from Mappls. The Place Search plugin for Mappls Web Map JS library is provided as a means to enable searching of Places on Mappls Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include Mappls Places JS in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to search for places directly with or without Mappls Maps visual interface.
2. A mappls.search() method to initiate search across all types places available on Mappls.
3. Ability to get information from Mappls Place Search plugin through a callback
4. Include the Place Search Plugin with or without an interactive Map component.


## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placesearch/mappls-placesearch-plugin)



###  Add the Place Search plugin

### Implementation

## React

```js
import { mappls } from "mappls-web-maps";
import { mappls_plugin } from "mappls-web-maps";
function App() {
  const auto = { width: "300px", position: "absolute",zIndex: 999,  fontSize: "15px",  padding: "10px", border: "1px solid #ddd", outline: "none !important"}
  
  var callback;
  var mapplsClassObject = new mappls();
  var mapplsPluginObject = new mappls_plugin();

const loadObject = {
  map: true,
  plugins: ["search"],
};

  mapplsClassObject.initialize(
    "<-----add token here--->",
    loadObject,
    () => {
      var optional_config = {
        location: [28.61, 77.23],
        region: "IND",
        height: 300,
      };
      mapplsPluginObject.search(
        document.getElementById("auto"),
        optional_config,
        callback
      );
    }
  );
  callback = (data) => {
    console.log(data);
  };

  return (
    <div>
      <input style={auto}
        type="text"
        id="auto"
        name="auto"
        className="search-outer form-control as-input"
        placeholder="Search places or eLoc's..."
        required=""
        spellCheck="false"
        
      />
    </div>
  );
}
export default App;
```
## Angular
```js
import { Component, OnInit } from '@angular/core';
import { mappls, mappls_plugin } from 'mappls-web-maps';
@Component({
  selector: 'app-root',
  template: `
    <style>
      #auto { color: #000; max-width: 99%; width: 300px; position: absolute; z-index: 999; font-size: 15px; padding: 10px; border: 1px solid #ddd; outline: none !important; top: 5px; border-radius: 10px; margin: 4px; }
    </style>
    <div
      id="map"
      style="width: 99%; height: 99vh; background-color: white;"
    ></div>
    <input
      type="text"
      id="auto"
      name="auto"
      class="search-outer form-control as-input"
      placeholder="Search places or eLoc's..."
      required=""
      spellcheck="false"
    />
  `,
  styleUrls: ['./app.component.css'],
})
export class AppComponent implements OnInit {
  mapObject: any;
  marker: any;
  callback: any;
  data: any;
  mapplsClassObject = new mappls();
  mapplsPluginObject = new mappls_plugin();

  ngOnInit() {
    const loadObject = {
      map: false,
      plugins: ['search'],
    };

    this.mapplsClassObject.initialize(
      '<----- Add your token here ------>',
      loadObject,
      () => {
        //
        var optional_config = {
          location: [28.61, 77.23],
          region: 'IND',
          height: 300,
        };
        this.mapplsPluginObject.search(
          document.getElementById('auto'),
          optional_config,
          this.callback
        );
      }
    );

    this.callback = (data: any) => {
      console.log(data);
    };
  }
}
```

#### Mandatory Parameters
1. `inputQuery`: The string which will be passed as input query to the search engine.

#### Optional Parameters
1. `Place Options`: Optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `pod`: Place type which you want to restrict the results by. e.g. `pod:'city'`. Valid values are: 
        - SLC (sub locality)
        - LC (locality)
        - CITY
        - VLG (village)
        - SDIST (sub district)
        - DIST (district)
        - STATE
        - SSLC (sub sub locality)
    - `filter`: a parameter to restrict results by. e.g. `filter:'cop:9qgxam'`
        - Can be used to filter results by PIN code. e.g. `pin:110055`
        - Can be used to filter results by eLoc. e.g. `cop:9qgxam`
        - Can be used to filter results by view bound. e.g. `filter=bounds:28.598882,77.212407;28.467375,77.353513`
    - `bridge`: initiates a bridge to be created to provide applicable nearby API searches. Involves using Nearby Search Plugin in conjunction with Place Search Plugin.
    - `hyperLocal`:This parameter lets the search give results that are hyper-localized to the reference location passed in the location parameter. This means that nearby                          results are given higher ranking than results far from the reference location. Highly prominent results will still appear in the search results, however theu                    will be lower in the list of results. This parameter will work ONLY in conjunction with the location parameter.
    - `tokenizeAddress`: boolean value used to return address tokens from the searched places from Mappls Search APIs. e.g. `tokenizeAddress:true`
    - `distance`: boolean value used to show aerial distance from location passed in `location`. of the searched place in results listing e.g. `distance:true`
    - `geolocation` : boolean value used to enable or disable current location selection . Default is true.
    - `width`: width of the suggested div. e.g. `width:300`
    - `height`: height of the suggested div. e.g `height:300`
    - `clearButton` : clear the value of input box. Default is true.
2. `callback`: callback to get results/error after call or selection.
3. `blank_callback` : callback when user clicks the cross button or erase the value of input box.

<br>

### 2. Calling Mappls Place Search for programmatically fixed text

Following is an example of calling Mappls.search() method programmatically for a fixed text rather than depending on a UI driven approach: 

```js
/*CALL for fix text - LIKE THIS*/
    var search = this.mapplsPluginObject.search("agra",placeOptions,callback);
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

