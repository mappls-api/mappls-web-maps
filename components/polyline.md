
[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova

# Polyline
 
### 1. Adding a Polyline

```js
this.polylineObject = this.mapplsClassObject.Polyline({
map:this.mapObject,
path:[{lat:28.55108, lng:77.26913},{lat:28.55185, lng:77.2675},{lat:28.5519, lng:77.2675},{lat:28.55193, lng:77.2675},{lat:28.55195, lng:77.26752}],
})
```
- Optional Code with all other polyline properties

```js
editable:  true, // makes polyline editable
gradient:[0, 'pink',0.1, 'black',0.3, 'cyan',0.5, 'lime',0.7, 'yellow',1, 'red'], //gradient polyline
strokeColor:  '#333'  // polyline color
strokeWeight:4, // stroke/ width of polyline
strokeOpacity:0.5, // opacity
lineGap:  0, // linegap
fitbounds:  true, // make map fit to polyline cordinates
fitboundOptions:{padding:  120,duration:1000, maxZoom:19}, //fitbound options
popupHtml:  'Route 1', // polyline popup
popupOptions: {offset: {'bottom': [0, -20]}}, //popup options
dasharray: [1,1]. // dashed polyline
visibility: false, // whether to show the Polyline or not.
zIndex:  5 , // priority index of the polyline.

// animated polyline
animate: {path:true/false,speed:5}

```
 
## 2. Polyline Events

-  **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
	 Example :  Angular / Cordova / Ionic *// Refer below code  without `this.` for React js reference.*
	```js
	this.polylineObject.addListener('load', function () { console.log('click');});
	```
-  **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  **drag:** Fired repeatedly during a "drag to pan" interaction.
-  **dragstart:** Fired when a "drag to pan" interaction starts.
-  **dragend:** Fired when a "drag to pan" interaction ends.
-  **mousemove:** Fired when mouse move.
-  **mouseout:** This event is fired when the mouse leaves the area of the marker icon..

  

### 3. Other Polyline Properties

### a) Animated Marker along the polyline

```js
var  pts=[{lat:28.55108, lng:77.26913},{lat:28.55106,lng:  77.26906},{lat:28.55105,lng:  77.26897},{lat:28.55101,lng:77.26872},{lat:28.55099, lng:77.26849},{lat:28.55097, lng:77.26831},{lat:28.55093, lng:77.26794},{lat:28.55089, lng:77.2676},{lat:28.55123, lng:77.26756},{lat:28.55145, lng:77.26758},{lat:28.55168, lng:77.26758},{lat:28.55175, lng:77.26759},{lat:28.55177, lng:77.26755},{lat:28.55179, lng:77.26753}];
this.polylineObject = this.mapplsClassObject.Polyline({
map:this.mapObject,
paths:  pts,
strokeColor:  '#333',
strokeOpacity:  1.0,
strokeWeight:  10,
fitbounds:true,
animate: {
speed:5
icon_width: 35 / “35”,
icon_height:  15 / “15”,,
icon_url: (icon_url),
repeat:  true/false,
},
});
```

### b) Multi Colored Polyline

```js
this.polylineObject = this.mapplsClassObject.Polyline({
map:  this.mapObject,
path: {
"type":  "FeatureCollection",
"features": [{
"type":  "Feature",
"properties": {
"color":  "green"
},
"geometry": {
"type":  "LineString",
"coordinates": [[28.55101,77.26872],[28.55099,77.26849],
[28.55097,77.26831],[28.55093, 77.26794],
[28.55089,77.2676],[28.55123,77.26756]]
}
},
{
"type":  "Feature",
"properties": {
"color":  "#F7455D"
},
"geometry": {
"type":  "LineString",
"coordinates": [[28.55123,77.26756],[28.55145,77.26758],
[28.55168,77.26758],[28.55168,77.26758],
[28.55168,77.26758],[28.55172,77.26759]]
}
}]
},
strokeColor:  red,
strokeOpacity:  1.0,
strokeWeight:  9,
fitbounds:  true, // or false
lineGap:  0,
fitboundOptions: {padding:  120,duration:1000},
popupHtml:  "Route 1",
popupOptions: {offset: {'bottom': [0, -20]}}
});
```

***Polyline Marker Animation Method***

```js
polylineObject.animate('stop'); //Stop Animation
polylineObject.animate('resume'); //Resume Animation
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