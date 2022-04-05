(For Internal purposes only as of 01-March-2022)

Instruction for the Reviewer
1) This is not final version, there are changes needs to be addressed
2) In some places there is mapmyindia URL for contact/signup/login that needs to be replaced with updated url.
3) Not all of the codes is tested for porper working (took some ref from Map SDK vector documentation that's why)
4) Ionic/Cordova section needs to be added

# Mappls Map SDK - NPM Package for Angular/React/Ionic/Cordova - Alpha 1

[<img src="https://about.mappls.com/api/img/mapmyindia-api.png" height="40"/> </p>](https://about.mappls.com/api/)

For full documentation contact Mappls here:
[apisupport@mappls.com](mailto:apisupport@mappls.com).

You can get your api key to be used in this document here: 
[https://apis.mappls.com/console/](https://apis.mappls.com/console/)

 

## Introduction
This is a NPM based packaged SDK which can be installed directly through NPM.
Create your own **Angular/React/Ionic-Cordova Based native app** powered by MapmyIndia Maps and deploy them to various platforms be it **web** or native **mobile** platforms.

Package name: mappls-maps

### Technologies
Node.js, Angular, Javascript,React JS, Cordova, Ionic

  

## Supported Platforms
- Web
- Android
- IOS

## Installation
```js
npm i mappls-maps
```

### Basic Import 
- ##### Angular : Import mappls class from "mappls-maps" package inside app.component.ts ( or other component of your use case ) .
```js
import { mappls } from 'mappls-maps'
```
- ##### React JS : Import mappls class from "mappls-maps" package inside app.js ( or other component of your use case ) .
```js
import { mappls } from 'mappls-maps'
```
- ##### Ionic Cordova : Add this plugin to your app's module(app.module.ts) and also include as a provider if you are using `IONIC V>1` ie. below
```js
import { mappls-maps } from 'mappls-maps';
@NgModule({
...
providers: [
...
mmi
...
]
...
})
export class AppModule { }
```

##  Usage

- #### React JS : Loading a Map

```js
import { mappls } from 'mappls-maps';
import './App.css';
 
function App() {
const styleMap = {width: '50%', height: '99vh', display:'inline-block'}
const mapProps = { center: [28.6330, 77.2194], traffic: false, zoom: 4, geolocation: false, clickableIcons: false }
  
let m = new mmi();
m.map({id:"map",key:"token/rest-key", properties: mapProps},maps.map({id:"map",key:"579638346fa47164a04b8e629a73994a", properties: mapProps},(data)=>{
m = data; //callback function return map obj
});

//load map layers/components after map load, inside this callback (Recommanded)

return (
<div>
<div id="map" style={style}></div>
</div>
);
}
export default App;
```  

- #### Angular : Loading a Map
```js
import { Component, OnInit } from '@angular/core';
import { mappls } from 'mappls-maps'
declare var m: any;

@Component({
selector: 'app-root',
templateUrl: './app.component.html',
styleUrls: ['./app.component.css']
})
  
export class AppComponent implements OnInit {
map_obj: any;
m = new mappls();

mapProps = { center: [28.6330, 77.2194], traffic: false, zoom: 4, geolocation: false, clickableIcons: false }  

ngOnInit(){
this.m.map({ id: "map", key:'token/rest-key', properties: this.mapProps}, (data: any)=>{
this.map_obj = data //callback function return map obj
//load maps layers/components after map load, inside this callback (Recommanded)
});
```

## Features

### Component :  1) Map
`map` method needs four parameters to initialize a map.

```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key', properties: {center: [28.6330, 77.2194]}}, (data)=>{ mapObject = data });
``` 
   
***i) Map div #id // with proper css width & height***
 
`id:'mapid'` **(mandatory)**
 
***ii) Token/Rest-Key to load the Map***

Key: `token/rest-key` your api map key from [Mapmyindia](https://apis.mappls.com/console/) **(mandatory)**

***iii) Map  Properties / Parameters***
```js
 properties:{ center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }
```
***iv) Callback Function***



### 1) General Usage
  -  Required Code
 ```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key', 
properties: {
center: [28.6330, 77.2194]}}, 

// Callback Method : Load all other components inside this it initilizes after map load
// it also returns map object
(data)=>{ mapObject = data }

);
```

 -  Optional Code with all other properties (code has to be modified to get it running)
 ```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key', 


properties: {                           //Properties Object

center: center: [28.544,77.5454], 
draggable: true,                      // toggle draggable map
zoom: 5,                              //The Initial Map `zoom` level.
minZoom: 8,                           // The minimum zoom level which will be displayed on the map
maxZoom: 15,                          // The maximum zoom level which will be displayed on the map


backgroundColor: '#fff',              // used for the background of the Map div.
heading: 100,                         // The `heading` for aerial imagery in degrees
traffic: true,                        // To show traffic control on map.
geolocation: true,                    // geolocation

// Coontrols
disableDoubleClickZoom: true,         // enables/disables zoom and center on double click.
fullscreenControl: true,              // It shows the icon of the full screen on the map
scrollWheel: true,                    // If false, disables zooming on the map using a mouse scroll 
scrollZoom: true,                     // if `false` scroll to zoom interaction is disabled.
rotateControl: true.                  // enable/disable 
rotateControlOptions: true,           // options for the Rotate control.

scaleControl: true,                   // The initial enabled/disabled state of the Scale control.
scaleControlOptions: true,            // options for the scaleControl
zoomControl: true					  // The enabled/disabled state of the Zoom control
zoomControlOptions: {position:mapppls.ControlPosition.RIGHT_CENTER},
//Possible Values : TOP_CENTER, `TOP_LEFT`, `TOP_RIGHT`, `LEFT_TOP`, `RIGHT_TOP`, `LEFT_CENTER`, `RIGHT_CENTER`,  `LEFT_BOTTOM`, `RIGHT_BOTTOM`, `BOTTOM_CENTER`, `BOTTOM_LEFT`, `BOTTOM_RIGHT``

clickableIcons: true,                 // A map icon represents a point of interest (POI)  
/*clickableIconsCallback: callBackMethod,*/  //Callback method :- callBackMethod(e){console.log(e);}
/*token_callback: token_callback,*/ 
// token_callback(e){ if(e.error='Token Expired') mapObj.setToken('newToken');console.log(e);}

indoor: true,                          // To show indoor floor plans in MapmyIndia Vector SDK. 
/*indoor_callback: show_ind, */          //Callback method :- show_ind(e){console.log(e);}
indoor_position: 'bottom-left',     
//Possible Values : TOP_CENTER, `TOP_LEFT`, `TOP_RIGHT`, `LEFT_TOP`, `RIGHT_TOP`, `LEFT_CENTER`, `RIGHT_CENTER`,  `LEFT_BOTTOM`, `RIGHT_BOTTOM`, `BOTTOM_CENTER`, `BOTTOM_LEFT`, `BOTTOM_RIGHT``
tilt: 30, 
//tilt : Controls the automatic switching behavior for the angle of incidence of the map. The only allowed values are 0 to 60. 
//The value 0 causes the map to always use a 0° overhead view regardless of the zoom level and viewport. The value 60 causes the tilt angle to 
//automatically switch to 60 whenever 60° imagery is available for the current zoom level and viewport, and switch back to 0 whenever 60° imagery is not available (this is the default behavior).


/*maxBounds:bounds */                    // Restrict map panning to an area
/*geolocation_callback:mmi, */           // call back for current location



//Uncomment these properties to get them running : clickableIconsCallback, token_callback, indoor_callback, maxBounds:bounds, geolocation_callback:mmi.
}, 


// Callback Method : Load all other components inside this it initilizes after map load
// it also returns map object
(data)=>{ mapObject = data }

```





### 2) Map Methods
 Suppose `mapObject` variable contains object of map() method which gets passed to it through callback of map() (see code below)
```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key', properties: {center: [28.6330, 77.2194]}}, (data)=>{ map = data });
```

> Below is General Javascript and React JS Usage
*> For Angular just add this to mapObject like this.mapObject.getBounds();*


***Example Usage***

```js
    mapObject.getBounds();
```

   
- **getBounds:** Returns the lat/lng bounds of the current viewport.
- **getCenter:** Returns the position displayed at the center of the map.
- **setCenter:** Sets the map's geographical centerpoint.
- **getDiv:** Returns the div on which map is set.
- **getHeading:** Returns the compass heading of aerial imagery.
- **getZoom:** Returns the current zoom level.
- **panBy:** Changes the center of the map by the given distance in pixels. If the distance is less than both the width and height of the map, the transition will be smoothly animated.
- **panTo:** Changes the center of the map to the given LatLng.
- **setheading:** Sets the compass heading for aerial imagery measured in degrees from cardinal direction North.
- **setZoom:** Sets the Zoom level of the current Map.
- **setTilt:** Controls the automatic switching behavior for the angle of incidence of the map. The only allowed values are 0 to 60. setTilt(0) causes the map to always use a 0° overhead view regardless of the zoom level and viewport. setTilt(60) causes the tilt angle to automatically switch to 60 whenever 60° imagery is available for the current zoom level and viewport, and switch back to 0 whenever 60° imagery is not available (this is the default behavior).
- **getTilt:** Returns the current angle of incidence of the map, in degrees from the viewport plane to the map plane. The result will be 0 for imagery taken directly overhead or 60 for 60° imagery.
- **isMoving:** Returns true if the map is panning, zooming, rotating, or pitching due to a camera animation or user gesture.
- **isRotating:** Returns true if the map is rotating due to a camera animation or user gesture.
- **addLayer:** A layer defines how data from a specified source will be styled. The JSON of layer to be passed in the addLayer.
- **removeLayer:** It removes the layer of the particular layerId you want to remove.
- **getLayer:** Returns the layer with the specified ID in the map's style.
- **moveLayer:** Moves a layer to a different z-position.```
- **indoor floor:** In case of indoor callback.
- **loaded:** Returns a Boolean indicating whether the map is fully loaded.
Returns `false` if the style is not yet fully loaded, or if there has been a change to the sources or style that has not yet fully loaded.
- **setToken:** Returns a Boolean indicating whether the token set or not.
Returns `false` if the token is not valid else return true.```


### 3) Map Events



#### Listening to Map Events via addListener() or on()

 
Suppose `mapObject` variable contains object of map() method which gets passed to it through callback of map() (see code below)
```js
mapplsClassObject.map({ id:  "map", key:'token/rest-key', properties: {center: [28.6330, 77.2194]}}, (data)=>{ mapObject = data });
```

> Below is General Javascript and React JS Usage
*> For Angular just add this to mapObject like this.mapObject.addListener('load', function () { console.log('load');});*

***Example Usage***

```js
    mapObject.addListener('load', function () { console.log('load');}); 
```
 **or**
 ```js
    mapObject.on('load', function () { console.log('load');}); 
```


- **load:** Fired when map is loadeed completely.
- **click:** Fired when a pointing device (usually a mouse) is pressed and released at the same point on the map.
- **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the map.
- **drag:** Fired repeatedly during a "drag to pan" interaction.
- **dragstart:** Fired when a "drag to pan" interaction starts.
- **dragend:** Fired when a "drag to pan" interaction ends.
- **idle:** Fired after the last frame rendered before the map enters an "idle" state:
    - No camera transitions are in progress
    - All currently requested tiles have loaded
    - All fade/transition animations have completed
- **mousemove:** Fired when a pointing device (usually a mouse) is moved within the map.
- **mouseout:** Fired when a point device (usually a mouse) leaves the map's canvas
- **mouseover:** Fired when a pointing device (usually a mouse) is moved within the map.
- **contextmenu:** Fired when the right button of the mouse is clicked or the context menu key is pressed within the map.
- **wheel:** Fired when a wheel event occurs within the map.
- **touchend:** Fired when a touchend event occurs within the map.
- **move:** Fired repeatedly during an animated transition from one view to another.
- **moveend:** Fired just after the map completes a transition from one view to another.
- **rotate:** Fired repeatedly during a "drag to rotate" interaction.
- **pitchend:** Fired immediately after the map's pitch (tilt) finishes changing as the result of either user interaction or methods.


   **Event System**:

1. `addListener:` Pass Event & Callback
2. `clearListeners:` Remove Event
3. `addListenerOnce:` Same as addListener but call once





  
## # Component : 2) RemoveLayer

### 1) General Usage
 
 ```js
mapplsClassObject.removeLayer({ map:  mapObject, layer:layerObject //marker, polyline etc Object });
```

 -  For Instance removing marker 
 ```js
 mapplsClassObject.removeLayer({ map:  mapObject, layer:markerObject });
```




  
## # Component : 3) Marker

### 1) General Usage
 

 - Required Code
 ```js
markerObject = mapplsClassObject.marker({
map: mapObject,
position:{lat:28.5512908, lng:77.26809282},
});
```

 -  Optional Code with all marker properties
 
```js
markerObject = mapplsClassObject.marker({
map: mapObject,
position:{lat:28.5512908, lng:77.26809282},

//Optional Properties
fitbounds: true, // Set View in which marker's plotted,
fitboundOptions: { padding:  120, duration:  1000 },   //fitbound options
icon:  'https://apis.mapmyindia.com/map_v3/2.png',     // icon url or Path
width: 25,                                             // marker's icon width
height: 40,                                            // marker's icon heigh

clusters:  true,                                        //clusters of marker when zoomed out
clustersOptions: { "color": "blue", "bgcolor": "red" },

offset: [0, 10],                                 // shift marker icon
popupHtml: 'Mapmyindia',                         // custom html for marker (<div> content </div>)
popupOptions: { openPopup: true, autoClose: true, maxWidth: 500} //popup options
cType : 0,                                // 0: for lat,lng combination (Default),1: for the opposite
});
```

### 2) Marker Methods
***How to use:-***
```js
    markerObject.setPosition({lat:28.454,lng:77.5454});
    markerObject.setIcon("https://apis.mapmyindia.com/map_v3/1.png");
```
- **setIcon:** Setting the URL of the icon. It replaces the icon URL.
- **setDraggable:** To make the marker draggable.
- **setPosition:** Setting the Position of the marker.
- **setZIndex:** Setting the priority index of the marker.
- **setPopup:** Setting Popup
- **getPosition:** Returns the compass heading of aerial imagery.


### 3) Marker Events

***How to use:-***

```js
   markerObject.addListener('load', function () { console.log('load');}); 
```
 **or**
 ```js
    markerObject.on('load', function () { console.log('load');}); 
```


- **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
- **cursor_changed:** Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
- **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
- **drag:** Fired repeatedly during a "drag to pan" interaction.
- **dragstart:** Fired when a "drag to pan" interaction starts.
- **dragend:** Fired when a "drag to pan" interaction ends.
- **draggable_changed:** This event is fired when the marker's draggable property changes.
- **mousedown:** This event is fired for a mousedown on the marker.
- **mouseout:** This event is fired when the mouse leaves the area of the marker icon..
- **mouseover:** This event is fired when the mouse enters the area of the marker icon.
- **mouseup:** This event is fired for a mouseup on the marker.


### 4) Other Marker Usage
#### i) Multiple Markers with cluster

```js
var geoData={
                "type": "FeatureCollection",
                "features": [{
                "type": "Feature",
                "properties": {"htmlPopup":"noida"},
                "geometry": {"type": "Point",
                "coordinates": [28.544,77.5454]}
                },{
                "type": "Feature",
                "properties": {"htmlPopup":"faridabad"},
                "geometry": {"type": "Point",
                "coordinates": [28.27189158,77.2158203125]}
                },{
                "type": "Feature",
                "properties": {"htmlPopup":"delhi"},
                "geometry": {"type": "Point",
                "coordinates": [28.549511,77.2678250]}
                }]
            };
     markerObject = mapplsClassObject.marker({map:mapObject,position:geoData,icon:'https://apis.mapmyindia.com/map_v3/1.png',clusters:true,fitbounds:true,fitboundOptions:{padding: 120,duration:1000},popupOptions:{offset: {'bottom': [0, -20]}}});
```
    
#### ii)  GeoJSON bulk Markers

```js
var geoData={
				"type": "FeatureCollection",
				"features": [{
				"type": "Feature",
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
				"geometry": {"type": "Point",
				"coordinates": [28.544,77.5454]}
				},{
				"type": "Feature",
				"properties": {"description":"faridabad","icon":"https://apis.mapmyindia.com/map_v3/1.png"},
				"geometry": {"type": "Point",
				"coordinates": [28.27189158,77.2158203125]}
				},{
				"type": "Feature",
				"properties": {"description":"delhi","icon":"https://apis.mapmyindia.com/map_v3/1.png"},
				"geometry": {"type": "Point",
				"coordinates": [28.549511,77.2678250]}
				}]
			};
	var markerObject=mapplsClassObject.addGeoJson({mapObject,data:geoData,fitbounds:true,cType:0});
```





## # Component : 4) InfoWindow

### 1) General Usage

```js
infowindowObject = mapplsClassObject.InfoWindow({
map:mapObject,                                //mapObject to plot infowindow
position: {"lat":  "28.552097968260668" ,"lng":  "77.2701604561851"},      
content:  "MMI Infowindow",                 // Content of infowindow

//Opotional Parameters
class: info_class ,           //class                        
offset: [0,10],               //Offset 
maxWidth:  300,               //Max Width of popup
closeButton: true             //Close button on infoWindow
})
```



## # Component : 5) Polyline

### 1) General Usage
 

 - Required Code 
 ```js
polylineObject = mapplsClassObject.Polyline({
map:mapObject,
path:[{lat:28.55108, lng:77.26913},{lat:28.55185, lng:77.2675},{lat:28.5519, lng:77.2675},{lat:28.55193, lng:77.2675},{lat:28.55195, lng:77.26752}], 
})
```

 -  Optional Code with all other polyline properties
 
```js
polylineObject = mapplsClassObject.Polyline({
map:mapObject,                                  //map Object
path:[{lat:28.55108, lng:77.26913},{lat:28.55185, lng:77.2675},{lat:28.5519, lng:77.2675},{lat:28.55193, lng:77.2675},{lat:28.55195, lng:77.26752}],     //path

editable: true,                          // makes polyline editable
gradient:[0, 'pink',0.1, 'black',0.3, 'cyan',0.5, 'lime',0.7, 'yellow',1, 'red'], //gradient polyline
 
strokeColor: '#333'                       // polyline color
strokeWeight:4,                           // stroke/ width of polyline
strokeOpacity:0.5,                        // opacity
lineGap:  0,                              // linegap
fitbounds:  true,                         // make map fit to polyline cordinates
fitboundOptions:{padding:  120,duration:1000, maxZoom:19},    //fitbound options
popupHtml:  'Route 1',                    // polyline popup
popupOptions: {offset: {'bottom': [0, -20]}},         //popup options
dasharray: [1,1].                         // dashed polyline
visibility: false,                        // whether to show the Polyline or not.
zIndex: 5 ,                               // priority index of the polyline.

 // animated polyline
animate: {path:true/false,speed:5}       
 
 
});
```

### 2) Polyline Events

***How to use:-***

```js
   polylineObject.addListener('load', function () { console.log('click');}); 
```
 **or**
 ```js
    polylineObject.on('load', function () { console.log('click');}); 
```


- **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
- **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
- **drag:** Fired repeatedly during a "drag to pan" interaction.
- **dragstart:** Fired when a "drag to pan" interaction starts.
-  **dragend:** Fired when a "drag to pan" interaction ends.
- **mousemove:** Fired when mouse move.
- **mouseout:** This event is fired when the mouse leaves the area of the marker icon..

### 3) Other Polyline Usage
#### i)  Animated Marker along the polyline
```js
 var pts=[{lat:28.55108, lng:77.26913},{lat:28.55106,lng: 77.26906},{lat:28.55105,lng: 77.26897},{lat:28.55101,lng:77.26872},{lat:28.55099, lng:77.26849},{lat:28.55097, lng:77.26831},{lat:28.55093, lng:77.26794},{lat:28.55089, lng:77.2676},{lat:28.55123, lng:77.26756},{lat:28.55145, lng:77.26758},{lat:28.55168, lng:77.26758},{lat:28.55175, lng:77.26759},{lat:28.55177, lng:77.26755},{lat:28.55179, lng:77.26753}];
        polylineObject = mapplsClassObject.Polyline({
        map:mapObject,
        paths: pts,
        strokeColor: '#333',
        strokeOpacity: 1.0,
        strokeWeight: 10,
        fitbounds:true,
        animate: { 
        speed:5 
        icon_width: 35 / “35”,
        icon_height: 15 / “15”,,
        icon_url: (icon_url),
        repeat: true/false,
    	},
    });
```
#### ii)  Multi Coloured Polyline
```js
polylineObject = mapplsClassObject.Polyline({
		map: mapObject,
		path: {
				"type": "FeatureCollection",
				"features": [{
					"type": "Feature",
					"properties": {
						"color": "green" 
						},
					"geometry": {
						"type": "LineString",
							"coordinates": [[28.55101,77.26872],[28.55099,77.26849],
							[28.55097,77.26831],[28.55093, 77.26794],
							[28.55089,77.2676],[28.55123,77.26756]]
						}
					},
					{
					"type": "Feature",
					"properties": {
						"color": "#F7455D" 
						},
					"geometry": {
						"type": "LineString",
							"coordinates": [[28.55123,77.26756],[28.55145,77.26758],
							[28.55168,77.26758],[28.55168,77.26758],
							[28.55168,77.26758],[28.55172,77.26759]]
						}
					}]
				},
		strokeColor: red,
		strokeOpacity: 1.0,
		strokeWeight: 9,
		fitbounds: true, // or false
		lineGap: 0,
		fitboundOptions: {padding: 120,duration:1000},
		popupHtml: "Route 1",
		popupOptions: {offset: {'bottom': [0, -20]}}
	});
```
***Polyline Marker Animation Method***
```js
polylineObject.animate('stop');         //Stop Animation
polylineObject.animate('resume');       //Resumne Animation
```


## # Component : 6) Polygon

### 1) General Usage
 

 - Mandatory Code
 ```js
polygonObject  =  mapplsClassObject.Polygon({
map:mapObject,
paths: [ {"lng":"77.26872","lat":  "28.55101"}, {"lng":"77.26849","lat":"28.55099"}, {"lng":"77.26831","lat":"28.55097"},
{"lng":"77.26794","lat":"28.55093"}, {"lng":"77.2676","lat":"28.55089"}, {"lng":"77.26756","lat":"28.55123"},
{"lng":"77.26758","lat":"28.55145"}, {"lng":"77.26758","lat":"28.55168"}, {"lng":"77.26759","lat":"28.55172"} ],

});
```

 -  Optional Code with all marker properties
 
```js
polygonObject  =  mapplsClassObject.Polygon({
map:mapObject,
paths: [ {"lng":"77.26872","lat":  "28.55101"}, {"lng":"77.26849","lat":"28.55099"}, {"lng":"77.26831","lat":"28.55097"},
{"lng":"77.26794","lat":"28.55093"}, {"lng":"77.2676","lat":"28.55089"}, {"lng":"77.26756","lat":"28.55123"},
{"lng":"77.26758","lat":"28.55145"}, {"lng":"77.26758","lat":"28.55168"}, {"lng":"77.26759","lat":"28.55172"} ],

fillColor:  "red",
fillOpacity:  0.3,
strokeColor:  "red",
strokeOpacity:  0.8,
html:"MMI",
fitbounds:  true,
fitboundOptions: {padding:  120,duration:1000},
popupHtml:  'Route 1',
popupOptions: {offset: {'bottom': [0, -20]}},
center:{{ "lat": "17.355529", "lng": "78.493919"}} 
});
```

### 3) Polygon Events

***How to use:-***

```js
   polygonObject.addListener('load', function () { console.log('cick');}); 
```
 **or**
 ```js
    polygonObject.on('load', function () { console.log('click');}); 
```


- **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
- **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
- **drag:** Fired repeatedly during a "drag to pan" interaction.
- **dragstart:** Fired when a "drag to pan" interaction starts.
- **dragend:** Fired when a "drag to pan" interaction ends.
- **draggable_changed:** This event is fired when the marker's draggable property changes..
- **mousemove:** Fired when mouse move.
- **mouseover:** This event is fired when the mouse enters the area of the marker icon.


## # Component : 7) Circle

### 1) General Usage
 

 - Required Code
 ```js
circleObject = mapplsClassObject.Circle({
center: {"lat":  "28.552097968260668" ,"lng":  "77.2701604561851"},
map:this.maps,
radius:  50,
});
```

 -  Optional Code with all other properties
 
```js
circleObject = mapplsClassObject.Circle({
center: {"lat":  "28.552097968260668" ,"lng":  "77.2701604561851"},
map:this.maps,
radius:  50,
strokeColor:  "red",
strokeOpacity:  0.8,
strokeWeight:  2,
fillColor:  "red",
fillOpacity:  0.3,
text:'kumar',
'text-color':'black',
'text-size':'30px'
});
```
### 3) Circle Events

***How to use:-***

```js
   circleObject.addListener('load', function () { console.log('click');}); 
```
 **or**
 ```js
    markerObject.on('load', function () { console.log('click');}); 
```


- **click:** Fired when a pointing device (usually a mouse) is pressed on the marker.
- **cursor_changed:** Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
- **dblclick:** Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
- **drag:** Fired repeatedly during a "drag to pan" interaction.
- **dragstart:** Fired when a "drag to pan" interaction starts.
- **dragend:** Fired when a "drag to pan" interaction ends.
- **draggable_changed:** This event is fired when the marker's draggable property changes.
- **mousemove:** Fired when mouse move.
- **mouseover:** This event is fired when the mouse enters the area of the marker icon.


## # Component : 8) Heatmap Layer

### 1) General Usage

 ```js
heatmapObject = mapplsClassObject.HeatmapLayer({
map:mapObject,
data:[ {lat:  28.550144, lng:  77.263927}, {lat:  28.549637, lng:  77.264144} ],
opacity:1,
radius:10,
maxIntensity:10,
fitbounds:true,
gradient: [ 'rgba(0, 255, 255, 0)', 'rgba(0, 255, 255, 1)' ]
})
});
```

## # Component : 8) GeoJson Layer

### 1) General Usage
 ```js
 var mixjson={ 
		"type": "FeatureCollection", 
		"features": [
			{ 
				"type": "Feature", 
				"geometry": {
					"type": "Point",
					"coordinates": [ 77.268038, 28.549652, 0 ] 
					}, 
				"properties": { 
					"name": "MapmyIndia old Office", 
					"description": "Okhla delhi", 
					"styleUrl": "#mmi_office", 
					"styleHash": "-3cca3c32", 
					"icon": "1.png", 
					"stroke": "#33CC00", 
					"stroke-opacity": 0.6509803921568628, 
					"stroke-width": 10, 
					"fill": "#FF0000", 
					"fill-opacity": 0.10196078431372549 
					} 
			}, 
			{ 
				"type": "Feature", 
				"geometry": { 
					"type": "Point", 
					"coordinates": [ 77.268952, 28.5510446, 0 ] 
					}, 
				"properties": { 
					"name": "MapmyIndia New Office", 
					"description": "68,Okhla delhi", 
					"styleUrl": "#mmi_office", 
					"styleHash": "-3cca3c32", 
					"icon": "1.png", 
					"stroke": "#33CC00", 
					"stroke-opacity": 0.6509803921568628, 
					"stroke-width": 10, 
					"fill": "#FF0000", 
					"fill-opacity": 0.10196078431372549 
					} 
			}, 
			{ 
				"type": "Feature", 
				"geometry": { 
					"type": "LineString", 
					"coordinates": [[ 77.268953, 28.551042 ], [ 77.268649, 28.551005 ], 
						[ 77.268392, 28.550986 ], [ 77.268231, 28.550967 ], 
						[ 77.268177, 28.550967 ], [ 77.268016, 28.550958 ], 
						[ 77.267587, 28.55092 ], [ 77.267651, 28.550722 ], 
						[ 77.267823, 28.55042 ], [ 77.267802, 28.550128 ], 
						[ 77.267995, 28.549751 ], [ 77.268039, 28.549652 ]]
					}, 
				"properties": { 
					"name": "Direction1", 
					"styleUrl": "#mmi_office", 
					"styleHash": "-3cca3c32", 
					"icon": "1.png", 
					"description": "Direction2", 
					"stroke": "#33CC00", 
					"stroke-opacity": 0.6509803921568628, 
					"stroke-width": 10, 
					"fill": "#FF0000", 
					"fill-opacity": 1.10196078431372549 
					} 
				}, 
				{ 
					"type": "Feature", 
					"geometry": { 
						"type": "Polygon", 
						"coordinates": [[ 77.2687822, 28.550868 ],[ 77.268996, 28.550868 ],
							[ 77.269039, 28.550383 ], [ 77.268835, 28.550388]] 
						}, 
					"properties": { 
						"name": "MapmyIndia Head Office", 
						"styleUrl": "#mmi_area", 
						"styleHash": "5617b970", 
						"stroke": "#33CC00", 
						"stroke-opacity": 0.6509803921568628, 
						"stroke-width": 3, 
						"fill": "#33CC00", 
						"fill-opacity": 0.6509803921568628 
						} 
				}] 
		};
geoJsonObject = mapplsClassObject.addGeoJson({
map:mapObject,
data:mixjson,
overlap:false,
fitbounds:true,
preserveViewport:true
});
```

#### Additional Properties for Markers

```js
	"icon": "1.png",  //for customizing marker
	"icon-size":1,  // size percentage of the marker: ranging from 
	"text":"2",  // text on marker
	"text-size":10,  // font size on marker
	"text-offset":[0,0],  //map anchor offset from the center of icon image.
	"text-color":"red" //color of text on marker
```


## # Component : 10)  KML Overlay

### 1) General Usage
 ```js
 var url="https://www.mapmyindia.com/api/advanced-maps/doc/sample/mmi.kml";
 
kmlObject = mapplsClassObject.KmlLayer({
map:mapObject,
url:url,
cType:0,
fitbounds:true,
fitboundOptions: {padding: 120,duration:1000}
preserveViewport:true
});
```

### Supported Object Types
**i. Markers**
**ii. Polylines**
**iii. Polygons**

<br>

## Version History

  
| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.2.1 | March 2022 | Mappls API Team ([BM](https://github.com/balmukandpathak)) 

<br></br>

### <-----end-of-document----->
  
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

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://www.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://www.mappls.com/pdf/mappls-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://www.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://www.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>