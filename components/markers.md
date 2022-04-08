[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova  

## Markers
  

###  1.  Adding a Marker
  - Angular / Cordova / Ionic

```js
this.markerObject = this.mapplsClassObject.marker({
map:  this.mapObject,
position:{lat:28.5512908, lng:77.26809282},
});
```
   - React js

```js
markerObject = mapplsClassObject.marker({
map:  mapObject,
position:{lat:28.5512908, lng:77.26809282},
});
```

- Optional Marker properties

```js
fitbounds:  true, // Set View in which marker's plotted,
fitboundOptions: { padding:  120, duration:  1000 }, //fitbound options
icon:  'https://apis.mapmyindia.com/map_v3/2.png', // icon url or Path
width:  25, // marker's icon width
height:  40, // marker's icon heigh
clusters:  true, //clusters of marker when zoomed out
clustersOptions: { "color":  "blue", "bgcolor":  "red" },
offset: [0, 10], // shift marker icon
popupHtml:  'MapmyIndia', // custom html for marker (<div> content </div>)
popupOptions: { openPopup:  true, autoClose:  true, maxWidth:  500} //popup options
cType : 0, // 0: for lat,lng combination (Default),1: for the opposite
});
```
 

### 2. Marker Methods
- Angular / Cordova / Ionic
```js
this.markerObject.setPosition({lat:28.454,lng:77.5454});
this.markerObject.setIcon("https://apis.mapmyindia.com/map_v3/1.png");
```
 - React js
```js
markerObject.setPosition({lat:28.454,lng:77.5454});
markerObject.setIcon("https://apis.mapmyindia.com/map_v3/1.png");
```

-  **setIcon:** Setting the URL of the icon. It replaces the icon URL.
-  **setDraggable:** To make the marker draggable.
-  **setPosition:** Setting the Position of the marker.
-  **setZIndex:** Setting the priority index of the marker.
-  **setPopup:** Setting Popup
-  **getPosition:** Returns the compass heading of aerial imagery.

  

### 3. Marker Events
- Angular / Cordova / Ionic

```js
this.markerObject.addListener('load', function () { console.log('load');});
```
- React js 

```js
markerObject.addListener('load', function () { console.log('load');});
```

-  **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
-  **cursor_changed:** Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
-  **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  **drag:** Fired repeatedly during a "drag to pan" interaction.
-  **dragstart:** Fired when a "drag to pan" interaction starts.
-  **dragend:** Fired when a "drag to pan" interaction ends.
-  **draggable_changed:** This event is fired when the marker's draggable property changes.
-  **mousedown:** This event is fired for a mousedown on the marker.
-  **mouseout:** This event is fired when the mouse leaves the area of the marker icon..
-  **mouseover:** This event is fired when the mouse enters the area of the marker icon.
-  **mouseup:** This event is fired for a mouseup on the marker.
  

### IV. Adding Multiple Markers

###    a) Multiple Markers as Cluster


Example :  Angular *// Refer below code  without `this.` for React js reference.*
```js
var  geoData={
"type":  "FeatureCollection",
"features": [{
"type":  "Feature",
"properties": {"htmlPopup":"noida"},
"geometry": {"type":  "Point",
"coordinates": [28.544,77.5454]}
},{
"type":  "Feature",
"properties": {"htmlPopup":"faridabad"},
"geometry": {"type":  "Point",
"coordinates": [28.27189158,77.2158203125]}
},{
"type":  "Feature",
"properties": {"htmlPopup":"delhi"},
"geometry": {"type":  "Point",
"coordinates": [28.549511,77.2678250]}
}]
};

this.markerObject = this.mapplsClassObject.marker({map:this.mapObject,position:geoData,icon:'https://apis.mapmyindia.com/map_v3/1.png',clusters:true,fitbounds:true,fitboundOptions:{padding:  120,duration:1000},popupOptions:{offset: {'bottom': [0, -20]}}}); 
```

### b) Multiple Markers as Geojson
 Example :  Angular / Cordova / Ionic *// Refer below code  without `this.` for React js reference.*

```js
var  geoData={
"type":  "FeatureCollection",
"features": [{
"type":  "Feature",
"properties":
{
"description":"noida",
"icon":"https://apis.mapmyindia.com/map_v3/1.png",
"icon-size":.75,
"icon-offset":[0,-10],
"text":"1",
"text-size":10,
"text-offset":[0,.6]
},
"geometry": {"type":  "Point",
"coordinates": [28.544,77.5454]}
},{
"type":  "Feature",
"properties": {"description":"faridabad","icon":"https://apis.mapmyindia.com/map_v3/1.png"},
"geometry": {"type":  "Point",
"coordinates": [28.27189158,77.2158203125]}
},{
"type":  "Feature",
"properties": {"description":"delhi","icon":"https://apis.mapmyindia.com/map_v3/1.png"},
"geometry": {"type":  "Point",
"coordinates": [28.549511,77.2678250]}
}]
};
var  this.markerObject=this.mapplsClassObject.addGeoJson({map:this.mapObject,data:geoData,fitbounds:true,cType:0});

```
  
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


> © Copyright 2022 CE Info Systems Ltd. All Rights Reserved. | [Terms & Conditions](http://www.mapmyindia.com/api/terms-&-conditions)