[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)

# Place Picker Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Place Picker Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-placepicker-plugin) 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 3.0 | 22 April 2022 | Mappls API Team ([MS](https://github.com/mamtasharma117)) |


## Introduction

A simple plugin / widget to pick places from the map. This SDK also has integrated Place Picker Plugin as optional component that enables one to narrow down to picked place by searching for it first and then changing the position of the resulting point on map to fine-tune the results.

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include Mappls Places JS in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to pick or search places directly with or without Mappls Maps visual interface.
2. A mappls.placePicker() method to initiate the plugin and pick places from Mappls Maps.
3. Ability to get information from Mappls Place Picker plugin through a callback.
4. Include the Place Picker Plugin with or without an interactive Map component.


## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-placepicker-plugin)




## Add the Place Picker plugin

```js
    var options={
                  map:this.mapObject,
                  callback:callback_method,
                  location:{lat:28.8787,lng:77.08888},
                  search:true,
                  
                  };
                  var picker= this.mapplsPluginObject.placePicker(options, callback_method );
                  function callback_method(data: any){
                     console.log(data);
                 }
      
```

#### Mandatory Parameters
1. `Place Options`: any object containing any of the two following mandatory configurations values.
    - `map`: object > vector map or raster map object from respective Mappls Map JS
    ##### OR
    - `location`: (lat,lng) object // to get data without map.
2. `callback`: (method): to get data after location selection . If no callback method is specified, UI `GET` button will be hidden. In this case, the consuming app can get data by calling method `getData()`.

#### Optional Parameters
1. `Place Options`: any object containing optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `geolocation`: boolean value used to enable or disable current location selection . Default is true.
    - `closeBtn`: (boolean): to give the option to close Place Picker (including hiding the top bar that has search & lower bar area that has the 'Done' button and related sub-text). Default is `true`.
    - `closeBtn_callback`: A callback method that is called when user clicks on the close button at the top left. To provide a call to action upon user closing the Place Picker plugin and thus providing the ability to continue towards further action by the consuming app.
    - `search`: (boolean): To enable / disable the integrated Place Search plugin. Default is `true`.
    - `topText`: The banner text to show at the top as title of the Place Picker plugin. Default is `Place Picker`.
    - `pinImage`: (URL) The PIN icon on the map. 
    - `pinHeight`: (number). To adjust the placement of the PIN icon on the map.
<br>

### 2. Calling Mappls Place Picker for programmatically fixed text

Following is an example of calling Mappls.placePicker() method programmatically for a fixed pair of coordinates rather than depending on a UI driven approach: 

```js
/*CALL for coordinates - LIKE THIS*/
this.mapplsPluginObject.placePicker({location:{lat:28.9898,lng:77.9898}},callback);
```

### 3. Method for removing place picker plugin with callback from map
#### Method
`remove()`

```js
picker.remove();
```

### 4. Method for programmatically setting location within callback on map.
#### Method
`setLocation()`

```js
picker.setLocation({lat:28.42424,lng:77.232323});
```

### 5. Method for getting location data from Place Picker plugin.

#### Description
This method is especially useful if no callback is given in options.
As per the current status of the Place Picker plugin's UI (map view and placement of PIN on map), the location data is returned.

#### Method
`getLocation()`

```js
picker.getLocation();
```


### Response Structure of Place Picker Data

```js
{	
        area: "India", //country information
	city: "New Delhi", // city of the pinned place.
	district: "South East Delhi District", // district of the pinned place.
	formatted_address: "Industrial Estate Phase 1, New Delhi, Delhi, India", // complete formatted address of the pinned place.
        houseName: "Equalisatcon Pump House", // house name of the pinned place.
        houseNumber: "", // house number of the pinned place.
	lat: "28.5237002235929", // latitude of the pinned place as per input coordinates.
	lng: "77.28024601936342", // longitude of the pinned place as per input coordinates.
	locality: "Okhla Industrial Estate Phase 1", // locality number of the pinned place.
	pincode: "110020", // PIN of the pinned place.
	poi: "BSES", // POI reference for the pinned place.
	poi_dist: "78", // Referenced POI's distance from the pinned place.
	responsecode: 200, // Response code of the Place Plugin
	state: "Delhi", // state of the pinned place.
	street: "Unnamed Road", // Street reference for the pinned place.
	street_dist: "16", // Referenced street's distance from the pinned place.
	subDistrict: "Kalkaji", // subdistrict of the pinned place.
	subLocality: "Block C", // sublocality of the pinned place.
	subSubLocality: "", // subsublocality of the pinned place.
	village: "" // village of the pinned place.
}

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




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

