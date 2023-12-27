[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api) 

# Mappls Web Maps - For Angular/ Ionic / Cordova

#  Circle

<p>Circles are a method for designating an area on a map with minimal user interaction. A circle is characterized by just two key attributes:

- The central point of the circle, specified by its latitude and longitude coordinates.
- The radius of the circle.

With these two values, you can effortlessly outline a specific region of interest on a map.</p>

React JS Components Live Demo : https://codesandbox.io/p/sandbox/mappls-set-style-zmkzr4?file=%2Fsrc%2FApp.js

#### 1. Adding a Circle
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

#### 2. Circle Events
   
-  `click`: Fired when a pointing device (usually a mouse) is pressed on the marker.

	Example :  Angular / Cordova / Ionic *// Refer below code  without "`this.`" for React js reference.*
	```js
	this.circleObject.addListener('load', function () { console.log('click');});
	```
 -  `cursor_changed`: Fired when a pointing device (usually a mouse) is pressed and released at the same point on the marker.
-  `dblclick`: Fired when a pointing device (usually a mouse) is clicked twice at the same point on the marker.
-  `drag:` Fired repeatedly during a "drag to pan" interaction.
-  `dragstart:` Fired when a "drag to pan" interaction starts.
-  `dragend:` Fired when a "drag to pan" interaction ends.
-  `draggable_changed:` This event is fired when the marker's draggable property changes.
-  `mousemove:` Fired when mouse move.
-  `mouseover:` This event is fired when the mouse enters the area of the marker icon.

#### Removing a circle

```js
mapplsClassObject.removeLayer({
  map: mapObject,
  layer: circleObject,
});
```

#### **React JS Implementation**
```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

const CircleComponent = ({ map }) => {
  const circleRef = useRef(null);

  useEffect(() => {
    if (circleRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: circleRef.current });
    }
    circleRef.current = mapplsClassObject.Circle({
      map: map,
      center: { lat: "28.552097968260668", lng: "77.2701604561851" },
      radius: 50,
    });
  });
};

const App = () => {
  const map = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  useEffect(() => {
    mapplsClassObject.initialize("<Add your Token>", { map: true }, () => {
      if (map.current) {
        map.current.remove();
      }
      map.current = mapplsClassObject.Map({
        id: "map",
        properties: {
          center: [28.5520979682606, 77.27016045618],
          zoom: 16,
        },
      });
      map.current.on("load", () => {
        setIsMapLoaded(true);
      });
    });
  }, []);

  return (
    <div
      id="map"
      style={{ width: "100%", height: "99vh", display: "inline-block" }}
    >
      {isMapLoaded && <CircleComponent map={map.current} />}
    </div>
  );
};
export default App;
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
