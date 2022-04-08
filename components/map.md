[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova
# Map Components

## 1. Usage 

`map`  method - There are 4 mandatory parameters to use this method.

-   Map div #id  _// with proper css width & height_`*
-   Token/Rest-Key to load the Map
-   Map Properties
-   Callback Function

### Code Snippet

```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key',
properties: {
center: [28.6330, 77.2194]}},
// Callback Method : Load all other components inside this it initilizes after map load
// it also returns map object
(data)=>{ mapObject = data }
);
```

### Optional Parameters Usage
 There are several map parameters which can be used with map methods to meet any application requirements.

```js
mapplsClassObject.map({ id:  "map", key:'token',
properties: { //Properties Object
center:  [28.544,77.5454], // the coordinates as [lat, lon]
draggable:  true, // toggle draggable map
zoom:  5, //the initial Map `zoom` level.
minZoom:  8, //  minimum zoom level which will be displayed on the map
maxZoom:  15, //  maximum zoom level which will be displayed on the map
backgroundColor:  '#fff', // used for the background of the Map div.
heading:  100, // The `heading` for aerial imagery in degrees
traffic:  true, // To show traffic control on map.
geolocation:  true, // to display the icon for current location

// Controls
disableDoubleClickZoom:  true, // enables/disables zoom and center on double click.
fullscreenControl:  true, // It shows the icon of the full screen on the map
scrollWheel:  true, // If false, disables zooming on the map using a mouse scroll
scrollZoom:  true, // if `false` scroll to zoom interaction is disabled.
rotateControl:  true. // enable/disable of the map.
scaleControl:  true, // The initial enabled/disabled state of the Scale control.
zoomControl:  true  // The enabled/disabled Zoom control at a fixed position
zoomControlOptions: {position:mappls.ControlPosition.RIGHT_CENTER},
//Possible Values : TOP_CENTER, `TOP_LEFT`, `TOP_RIGHT`, `LEFT_TOP`, `RIGHT_TOP`, `LEFT_CENTER`, `RIGHT_CENTER`, `LEFT_BOTTOM`, `RIGHT_BOTTOM`, `BOTTOM_CENTER`, `BOTTOM_LEFT`, `BOTTOM_RIGHT``
clickableIcons:  true,  //to make the icons clickable
indoor:  true, // To show indoor floor plans in MapmyIndia Vector SDK.
indoor_position:  'bottom-left',
//Possible Values : TOP_CENTER, `TOP_LEFT`, `TOP_RIGHT`, `LEFT_TOP`, `RIGHT_TOP`, `LEFT_CENTER`, `RIGHT_CENTER`, `LEFT_BOTTOM`, `RIGHT_BOTTOM`, `BOTTOM_CENTER`, `BOTTOM_LEFT`, `BOTTOM_RIGHT``
tilt:  30,//tilt : Controls the automatic switching behavior for the angle of incidence of the map. The only allowed values are 0 to 85.
},
(data)=>{ mapObject = data }

```
## 2. Map Methods

-   `getBounds` :  Returns the lat/lng bounds of the current viewport.  
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getBounds();
    ```
    
    -   React js
    
    ```
        mapObject.getBounds();
    ```
    


-   `getCenter` :  Returns the position displayed at the center of the map in the form of coordinates.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getCenter();
    ```
    
    -   React js
    
    ```
        mapObject.getCenter();
    ```

-   `setCenter` :  Sets the map’s geographical center point.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.setCenter([77.2689,28.5507]);
    ```
    
    -   React js
    
    ```
        mapObject.setCenter([77.2689,28.5507]);
    ```
-   `getDiv` :  Returns the information of the div on which map is set.
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getDiv();
    ```
    
    -   React js
    
    ```
        mapObject.getDiv();
    ```
-   `getHeading` :  Returns the compass heading of aerial imagery.
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getHeading();
    ```
    
    -   React js
    
    ```
        mapObject.getHeading();
    ```
-   `getZoom` :  Returns the current zoom level.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getZoom();
    ```
    
    -   React js
    
    ```
        mapObject.getZoom();
    ```
-   `panBy` :  Changes the center of the map by the given distance in pixels. If the distance is less than both the width and height of the map, the transition will be smoothly animated.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.panBy([77.2689,28.5507]);
    ```
    
    -   React js
    
    ```
        mapObject.panBy([77.2689,28.5507]);
    ```

-   `panTo` :  Changes the center of the map to the given geolocation.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.panTo([77.2689,28.5507]);
    ```
    
    -   React js
    
    ```
        mapObject.panTo([77.2689,28.5507]);
    ```
-   `setheading` :  Sets the compass heading for aerial imagery measured in degrees from cardinal direction North.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.setheading(60);
    ```
    
    -   React js
    
    ```
        mapObject.setheading(60);
    ```
-   `setZoom` :  Sets the Zoom level of the current Map.

    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.setZoom(15);
    ```
    
    -   React js
    
    ```
        mapObject.setheading(15);

-   `setTilt` :  Controls the automatic switching behavior for the angle of incidence of the map. The only allowed values are 0 to 85.
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.setTilt(15);
    ```
    
    -   React js
    
    ```
        mapObject.setTilt(15);

-   `getTilt` :  Returns the current angle of incidence of the map, in degrees from the viewport plane to the map plane.
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.getTilt();
    ```
    
    -   React js
    
    ```
        mapObject.getTilt();
    ```
-   `loaded` :  Returns a Boolean indicating whether the map is fully loaded.  Returns  `false`  if the style is not yet fully loaded, or if there has been a change to the sources or style that has not yet fully loaded.
    _`Example Usage`_
    
    -   Angular / Cordova / Ionic
    
    ```
        this.mapObject.loaded();
    ```
    
    -   React js
    
    ```
        mapObject.loaded();
    ```
-   `setToken` : Returns a Boolean indicating whether the token set or not.  
    Returns  `false`  if the token is not valid else return true.


## 3.  Map Events -  Listening to Map Events



## `Event Types`:

1.  `addListener` :  To pass Event & callback
    
2.  `clearListeners` :  Used to remove Event
    
3.  `addListenerOnce` :  Same as addListener but call once


Lets Learn how to use them.

## 1. addListener

-  `load` :  Fired when map is loaded completely.

_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('load', function () { console.log('load');});

```

-   React js

```js
mapObject.addListener('load', function () { console.log('load');});

```

-   `click` :  Fired when a pointing device (usually a mouse) is pressed and released at the same point on the map.

_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('click', function () { console.log('click');});
```

-   React js

```js
mapObject.addListener('click', function () { console.log('load');});

```
    
-   `dblclick` :  Fired when a pointing device (usually a mouse) is clicked twice at the same point on the map.

_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('dblclick', function () { console.log('dblclick');});
```

-   React js

```js
mapObject.addListener('dblclick', function () { console.log('dblclick');});
```
    
-   `drag` :  Fired repeatedly during a “drag to pan” interaction.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('drag', function () { console.log('drag');});
```

-   React js

```js
mapObject.addListener('drag', function () { console.log('drag');});
```
    
-   `dragstart` :  Fired when a “drag to pan” interaction starts.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('dragstart', function () { console.log('dragstart');});
```

-   React js

```js
mapObject.addListener('dragstart', function () { console.log('dragstart');});
```
    
-   `dragend` :  Fired when a “drag to pan” interaction ends.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('dragend', function () { console.log('dragend');});
```

-   React js

```js
mapObject.addListener('dragend', function () { console.log('dragend');});
```
    
-   `idle` :  Fired after the last frame rendered before the map enters an “idle” state:
    
    -   No camera transitions are in progress
        
    -   All currently requested tiles have loaded
        
    -   All fade/transition animations have completed

_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('idle', function () { console.log('idle');});
```

-   React js

```js
mapObject.addListener('idle', function () { console.log('idle');});
```    
        
-   `mousemove` :  Fired when a pointing device (usually a mouse) is moved within the map.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('idle', function () { console.log('idle');});
```

-   React js

```js
mapObject.addListener('idle', function () { console.log('idle');});
``` 
    
-   `mouseout` :  Fired when a point device (usually a mouse) leaves the map’s canvas
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('idle', function () { console.log('idle');});
```

-   React js

```js
mapObject.addListener('idle', function () { console.log('idle');});
```     
-   `mouseover` :  Fired when a pointing device (usually a mouse) is moved within the map.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('mouseover', function () { console.log('mouseover');});
```

-   React js

```js
mapObject.addListener('mouseover', function () { console.log('mouseover');});
```     
-   `contextmenu` :  Fired when the right button of the mouse is clicked or the context menu key is pressed within the map.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('contextmenu', function () { console.log('contextmenu');});
```

-   React js

```js
mapObject.addListener('contextmenu', function () { console.log('contextmenu');});
```     
-   `wheel` :  Fired when a wheel event occurs within the map.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('wheel', function () { console.log('wheel');});
```

-   React js

```js
mapObject.addListener('wheel', function () { console.log('wheel');});
```     
-   `touchend` :  Fired when a touchend event occurs within the map.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('touchend', function () { console.log('touchend');});
```

-   React js

```js
mapObject.addListener('touchend', function () { console.log('touchend');});
```  

-   `move` :  Fired repeatedly during an animated transition from one view to another.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('move', function () { console.log('move');});
```

-   React js

```js
mapObject.addListener('move', function () { console.log('move');});
```      
-   `moveend` :  Fired just after the map completes a transition from one view to another.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('moveend', function () { console.log('moveend');});
```

-   React js

```js
mapObject.addListener('moveend', function () { console.log('moveend');});
```      
-   `rotate` :  Fired repeatedly during a “drag to rotate” interaction.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('rotate', function () { console.log('rotate');});
```

-   React js

```js
mapObject.addListener('rotate', function () { console.log('rotate');});
```      
-   `pitchend` :  Fired immediately after the map’s pitch (tilt) finishes changing as the result of either user interaction or methods.
_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.addListener('pitchend', function () { console.log('pitchend');});
```

-   React js

```js
mapObject.addListener('pitchend', function () { console.log('pitchend');});
```      

## 2. clearListeners

_`Example Usage`_

-   Angular / Cordova / Ionic

```js
this.mapObject.clearListeners('loaded', function () { console.log('unloaded');});
```

-   React js

```js
mapObject.removeListener('loaded', function () { console.log('unloaded');});
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