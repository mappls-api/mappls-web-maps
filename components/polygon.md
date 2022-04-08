[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova
# Polygon

  

### 1. Adding a Polygon

```js
this.polygonObject = this.mapplsClassObject.Polygon({
map:this.mapObject,
paths: [ {"lng":"77.26872","lat":  "28.55101"}, {"lng":"77.26849","lat":"28.55099"}, {"lng":"77.26831","lat":"28.55097"},
{"lng":"77.26794","lat":"28.55093"}, {"lng":"77.2676","lat":"28.55089"}, {"lng":"77.26756","lat":"28.55123"},
{"lng":"77.26758","lat":"28.55145"}, {"lng":"77.26758","lat":"28.55168"}, {"lng":"77.26759","lat":"28.55172"} ],
});
```
- Optional  Polygon properties

```js
fillColor:  "red",
fillOpacity:  0.3,
strokeColor:  "red",
strokeOpacity:  0.8,
html:"MMI",
fitbounds:  true,
fitboundOptions: {padding:  120,duration:1000},
popupHtml:  'Route 1',
popupOptions: {offset: {'bottom': [0, -20]}},
center:{{ "lat":  "17.355529", "lng":  "78.493919"}}
```

  

### 2.  Polygon Events
-  **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
	Example :  Angular / Cordova / Ionic *// Refer below code  without `this.` for React js reference.*
	```js
	polygonObject.addListener('load', function () { console.log('click');});
	```
-  **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  **drag:** Fired repeatedly during a "drag to pan" interaction.
-  **dragstart:** Fired when a "drag to pan" interaction starts.
-  **dragend:** Fired when a "drag to pan" interaction ends.
-  **draggable_changed:** This event is fired when the marker's draggable property changes..
-  **mousemove:** Fired when mouse move.
-  **mouseover:** This event is fired when the mouse enters the area of the marker icon.


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