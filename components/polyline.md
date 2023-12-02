[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api) 

# Mappls Web Maps - For Angular/ Ionic / Cordova

## Polyline
 <p>Polylines are a means of visualizing movement or routes on a map, and at Mappls, we recognize the various ways you can make use of a map's capabilities, with Polylines being one of them.

Polylines are essentially uninterrupted lines formed by one or more line segments, preferably represented as a geopath. To include a polyline, follow the initial map setup as described in the earlier sections, and then establish a dataset. What exactly is a dataset? It's the assembly of points (latitude and longitude coordinates) that defines the path along which you wish the polyline to be depicted.</p>


### 1. Adding a Polyline

```js
this.polylineObject = this.mapplsClassObject.Polyline(
	{
		map:this.mapObject,
		path:[
			{
				lat:28.55108, 
				lng:77.26913
			},
			{
				lat:28.55185, 
				lng:77.2675
			},
			{
				lat:28.5519, 
				lng:77.2675
			},
			{
				lat:28.55193, 
				lng:77.2675
			},
			{
				lat:28.55195, 
				lng:77.26752
			}],
	}
);
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
fitboundOptions:
	{
		padding:  120,
		duration:1000, 
		maxZoom:19
	}, //fitbound options
popupHtml:  'Route 1', // polyline popup
popupOptions: 
	{
		offset: 
			{
				'bottom': [0, -20]
			}
	}, //popup options
dasharray: [1,1]. // dashed polyline
visibility: false, // whether to show the Polyline or not.
zIndex:  5 , // priority index of the polyline.

// animated polyline
animate: 
	{
		path: true, //true or false
		speed: 5
	}
```
 
## 2. Polyline Events

-  `click`: Fired when a pointing device (usually a mouse) is pressed on the marker.
	 Example :  Angular / Cordova / Ionic *// Refer below code  without `this.` for React js reference.*
	```js
	this.polylineObject.addListener('load', function () { console.log('click');});
	```
-  `dblclick`: Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  `drag`: Fired repeatedly during a "drag to pan" interaction.
-  `dragstart`: Fired when a "drag to pan" interaction starts.
-  `dragend`: Fired when a "drag to pan" interaction ends.
-  `mousemove`: Fired when mouse move.
-  `mouseout`: This event is fired when the mouse leaves the area of the marker icon..

  

### 3. Other Polyline Properties

### a) Animated Marker along the polyline

```js
var  pts = 
[
	{
		lat:28.55108, 
		lng:77.26913
	},
	{
		lat:28.55106,
		lng:  77.26906
	},
	{
		lat:28.55105,
		lng:  77.26897
	},
	{
		lat:28.55101,
		lng:77.26872
	},
	{
		lat:28.55099, 
		lng:77.26849
	},
	{
		lat:28.55097, 
		lng:77.26831
	},
	{
		lat:28.55093, 
		lng:77.26794
	},
	{
		lat:28.55089, 
		lng:77.2676
	},
	{
		lat:28.55123, 
		lng:77.26756
	},
	{
		lat:28.55145, 
		lng:77.26758
	},
	{
		lat:28.55168, 
		lng:77.26758
	},
	{
		lat:28.55175, 
		lng:77.26759
	},
	{
		lat:28.55177, 
		lng:77.26755
	},
	{
		lat:28.55179, 
		lng:77.26753
	}
];
this.polylineObject = this.mapplsClassObject.Polyline(
	{
		map:this.mapObject,
		paths:  pts,
		strokeColor:  '#333',
		strokeOpacity:  1.0,
		strokeWeight:  10,
		fitbounds:true,
		animate: 
			{
				speed: 5
				icon_width: 35, // or as “35”
				icon_height:  15, // or as “15”,
				icon_url: (icon_url),
				repeat:  true //false,
			},
	}
);
```

### b) Multi Colored Polyline

```js
this.polylineObject = this.mapplsClassObject.Polyline(
	{
		map:  this.mapObject,
		path: 
			{
				"type": "FeatureCollection",
				"features": [
					{
						"type": "Feature",
						"properties": {
							"color": "green"
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[
									28.55101,
									77.26872
								],
								[
									28.55099,
									77.26849
								],
								[
									28.55097,
									77.26831
								],
								[
									28.55093,
									77.26794
								],
								[
									28.55089,
									77.2676
								],
								[
									28.55123,
									77.26756
								]
							]
						}
					},
					{
						"type": "Feature",
						"properties": {
							"color": "#F7455D"
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[
									28.55123,
									77.26756
								],
								[
									28.55145,
									77.26758
								],
								[
									28.55168,
									77.26758
								],
								[
									28.55168,
									77.26758
								],
								[
									28.55168,
									77.26758
								],
								[
									28.55172,
									77.26759
								]
							]
						}
					}
				]
			},
		strokeColor:  red,
		strokeOpacity:  1.0,
		strokeWeight:  9,
		fitbounds:  true, // or false
		lineGap:  0,
		fitboundOptions: 
			{
				padding:  120,
				duration:1000
			},
		popupHtml:  "Route 1",
		popupOptions: 
			{
				offset: 
					{
						'bottom': [0, -20]
					}
			}
	}
);
```

### Polyline Marker Animation Method

```js
polylineObject.animate('stop'); //Stop Animation
polylineObject.animate('resume'); //Resume Animation
```

### Remove polyline

```js
mapplsClassObject.removeLayer({
  map: mapObject,
  layer: polylineObject,
});
```


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
