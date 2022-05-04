

[![N|Solid](https://about.mappls.com/images/mappls-b-logo.svg)](https://www.mapmyindia.com/api/)


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
  
@Component({
selector:  'app-root',
template  :  '<div  id="map"  style="width: 99%; height: 99vh; background-color: white;"></div>',
styleUrls: ['./app.component.css']
})

export  class  AppComponent  implements  OnInit {
mapObject:  any;
mapplsClassObject =  new  mappls();
mapplsPluginObject =  new  mappls_plugin();

mapProps = { center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }

    ngOnInit() {
        this.mapplsClassObject.initialize("token",()=>{
            this.mapObject  =  this.mapplsClassObject.Map({id:  "map", properties:  this.mapProps});

            //load map layers/components after map load, inside this callback (Recommended)
            this.mapObject.on("load", ()=>{
            // Activites after mapload
            })

        });

        }

}
```

 -  #### React JS

```js
import { mappls } from  'mappls-web-maps';
function  App() {
const  styleMap  = {width:  '99%', height:  '99vh', display:'inline-block'}
const  mapProps  = { center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }
var mapObject ;
var mapplsClassObject=  new  mappls();

    mapplsClassObject.initialize("token",()=>{
        mapObject = mapplsClassObject.Map({id:  "map", properties: mapProps});

        //load map layers/components after map load, inside this callback (Recommended)
        mapObject.on("load", ()=>{
        // Activites after mapload
        })

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
 	- [Map](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md)
		 - [Properties ](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#1-properties)
		 - [Methods](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#2-map-methods)
		 - [Events](https://github.com/mappls-api/mappls-web-maps/blob/main/components/map.md#3--map-events----listening-to-map-events)
		 
	 - [Remove Layer]()
	 - [Markers](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md)
		 - [Adding a marker](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#1--adding-a-marker)
		 - [Marker Methods](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#2-marker-methods)
		 - [Marker Events](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#3-marker-events)
		 - [Adding Multiple Markers](https://github.com/mappls-api/mappls-web-maps/blob/main/components/markers.md#iv-adding-multiple-markers)
	 - [InfoWindows](https://github.com/mappls-api/mappls-web-maps/blob/main/components/infowindow.md)
	 - [Polylines](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
	 - [Polygons](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polygons.md)
	 - [Circle](https://github.com/mappls-api/mappls-web-maps/blob/main/components/circle.md)
	 - [Overlay](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
		 - [Geojson](https://github.com/mappls-api/mappls-web-maps/blob/main/components/polyline.md)
		 - [KML](https://github.com/mappls-api/mappls-web-maps/blob/main/components/overlays.md)
		 - [Heat Map](https://github.com/mappls-api/mappls-web-maps/blob/main/components/heatmap.md)
 - Plugins
	 - [Place Search](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/placeSearch-plugin)
	 - [Place Picker](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/placePicker-plugin)
	 - [Nearby Search](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/nearbySearch-plugin)
	 - [Directions](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/directions-plugin)
	 - [getDistance](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/getDistance%20Method)
	 - [marker-plugin](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/marker-plugin)
	- [Eloc-Plugin](https://github.com/mappls-api/mappls-web-maps/tree/main/plugins/eLoc-plugin)
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
