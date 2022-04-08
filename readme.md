

[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)

  
  
  
  

## Introduction

  

Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications

  
  

Explore through 238 nations with Global Search, Routing and Mapping APIs & SDKs powered with India's most comprehensive and robust mapping functionalities.

  

Create your own **Angular/React/Ionic/Cordova Based native app** powered by Mappls Maps and deploy them to various platforms be it **web** or native **mobile** platforms.

  

## **Package name** : mappls-web-maps

  

# Sign up for Mappls

  

Not a mappls user yet? [Sign up](https://apis.mappls.com/console/) for an account here. Once you’re signed in, all you need to start building is a mappls key. You can create and manage your access tokens on your Mappls Account page.

  

## API Usage

Your MapmyIndia Maps SDK usage needs a set of license keys [get them here ](https://apis.mappls.com/console/) and is governed by the API terms and conditions. As part of the terms and conditions, you cannot remove or hide the MapmyIndia logo and copyright information in your project. Please see branding guidelines on MapmyIndia website for more details. The allowed SDK hits are described on the plans page. Note that your usage is shared between platforms, so the API hits you make from a web application, Android app or an iOS app all add up to your allowed daily limit.

## Version History

  


| Version | Last Updated | Author | Remarks |
| ---- | ---- | ---- | ---- |
| 3.0 | 05 April 2022 | MapmyIndia API Team ([MS](https://github.com/mamtasharma117)) | Initial Commit |

  

###   Supported Technologies

Node.js, Angular, React JS, Cordova, Ionic

  
### Supported Platforms

- Web
- Android
- iOS

  

## Installation

```js
npm  i  mappls-web-maps
```

### Import Package

- ### Angular : Import mappls class from "mappls-web-maps" package i.e. app.component.ts ( or other component of your use case ) .

```js
import { mappls } from 'mappls-web-maps';
```

-  #### React JS : Import mappls class from "mappls-web-maps" package inside app.js ( or other component of your use case ) .

```js
import { mappls } from  'mappls-web-maps'
```
 

## Usage

### Loading a Map
  

-  #### Angular / Cordova / Ionic

```js
import { Component, OnInit } from  '@angular/core';
import { mappls } from  'mappls-web-maps'
declare  var m:  any;
@Component({
selector:  'app-root',
template  :  '<div  id="map"  style="width: 99%; height: 99vh; background-color: white;"></div>',
styleUrls: ['./app.component.css']
})
export  class  AppComponent  implements  OnInit {
mapObject:  any;
mapplsClassObject =  new  mappls();
mapProps = { center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }

ngOnInit(){
// Initilize map
this.mapplsClassObject.map({ id:  "map", key:"token/rest-key", properties:  this.mapProps}, (data:  any)=>{
this.mapObject  = data //callback function return map object
//load maps layers/components after map load, inside this callback (Recommended)
});
}
}
```

 -  #### React JS

```js
import { mappls } from  'mappls-webb-maps';
import  './App.css';
function  App() {
const  styleMap  = {width:  '99%', height:  '99vh', display:'inline-block'}
const  mapProps  = { center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }
var mapObject ;
var mapplsClassObject=  new  mappls();
mapplsClassObject.map({id:"map",key:"1da08b6a-dc0b-4d81-915e-2995278be995", properties: mapProps},(data)=>{
mapObject = data; //callback function return map obj
//load map layers/components after map load, inside this callback (Recommanded)
});
  
return (
<div>
<div  id="map"  style={styleMap}></div>
</div>
);
}
export  default  App;
```

  ## Learn about Features

 - Components
 	- [Map]()
		 - [Events]()
		 -  [Methods]()
		 - [Properties ]()
	 - [Remove Layer]()
	 - [Markers]()
		 - [Adding a marker]()
		 - [Adding Multiple Markers]()
	 - [InfoWindows]()
	 - [Polylines]()
	 - [Polygons]()
	 - [Circle]()
	 - [Overlay]()
		 - [Geojson]()
		 - [KML]()
		 - [Heat Map]()
 - Plugins
	 - [Place Search]()
	 - [Place Picker]()
	 - [Nearby Search]()
	 - [Directions]()
	 - [getDistance]()
	 - [marker-plugin]()
	- [placeDetails-Plugin]()
	- [routeSummary Plugin]()


That’s All !


  


  

![Email](https://cdn.mapmyindia.com/mappls_web/maps_widget_v2/images/mappls.svg)

  

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