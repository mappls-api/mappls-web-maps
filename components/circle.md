
[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova

#  Circle

  

## 1. Adding a Circle

```js
this.circleObject = this.mapplsClassObject.Circle({
center: {"lat":  "28.552097968260668" ,"lng":  "77.2701604561851"},
map:this.mapObject,
radius:  50,
});
```

- Optional Circle Properties

```js
strokeColor:  "red",
strokeOpacity:  0.8,
strokeWeight:  2,
fillColor:  "red",
fillOpacity:  0.3,
text:'MapmyIndia',
'text-color':'black',
'text-size':'30px'
```

## 2. Circle Events

   
-  **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
	Example :  Angular / Cordova / Ionic *// Refer below code  without `this.` for React js reference.*
	```js
	this.circleObject.addListener('load', function () { console.log('click');});
	```
 -  **cursor_changed:** Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
-  **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  **drag:** Fired repeatedly during a "drag to pan" interaction.
-  **dragstart:** Fired when a "drag to pan" interaction starts.
-  **dragend:** Fired when a "drag to pan" interaction ends.
-  **draggable_changed:** This event is fired when the marker's draggable property changes.
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