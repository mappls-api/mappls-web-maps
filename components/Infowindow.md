[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)

# Mappls Web Maps - For Angular/ Ionic / Cordova

#  InfoWindow  

Info Windows provide a user-friendly method for displaying information related to a marker, essentially explaining the purpose of that marker. When users encounter a marker, their natural instinct is to click on it to discover more details, and presenting an info window is the ideal approach to fulfill this expectation.

React JS Component Live Demo : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-infowindow-vxdy8p?file=%2Fsrc%2FApp.js%3A7%2C38)

#### Adding a InfoWindow
```js
this.infowindowObject = this.mapplsClassObject.InfoWindow(
    {
        map: this.mapObject, //mapObject to plot infowindow
        position: 
        {
            "lat":  "28.552097968260668" ,
            "lng":  "77.2701604561851"
        },
        content:  "MMI Infowindow", // Content of infowindow
        //Opotional Parameters
        class:  info_class , //class
        offset: [0,10], //Offset
        maxWidth:  300, //Max Width of popup
        closeButton:  true  //Close button on infoWindow
    }
)
``` 
#### Removing a InfoWindow

```js
mapplsClassObject.removeLayer({
    map: mapObject,
    layer: infowindowObject,
  });
```
#### **React JS Implementation** : 
```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

const InfoWindowComponent = ({ map }) => {
  const infowindowRef = useRef(null);

  useEffect(() => {
    if (infowindowRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: infowindowRef.current });
    }
    infowindowRef.current = mapplsClassObject.InfoWindow({
      map: map,
      content:
        '<div><div style="background-color:#191919;color:#fff;padding:5px;margin-top:2%;">MapmyIndia Head Office</div><p> Open 9AM & Closes 6:30PM Mon to Fri</p><br><p>Sat & Sun: Off</p></div>',
      position: {
        lat: 28.529467,
        lng: 77.22315,
      },
      offset: [0, 10], //Offset
      maxWidth: 300, //Max Width of popup
      closeButton: true, //Close button on infoWindow
    });
  });
};

const App = () => {
  const map = useRef(null);
  const [isMapLoaded, setIsMapLoaded] = useState(false);

  useEffect(() => {
    mapplsClassObject.initialize("<Authorization Token>", { map: true }, () => {
      if (map.current) {
        map.current.remove();
      }
      map.current = mapplsClassObject.Map({
        id: "map",
        properties: {
          center: [28.529467, 77.22315],
          zoom: 15,
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
      {isMapLoaded && <InfoWindowComponent map={map.current} />}
    </div>
  );
};
export default App;
```

<br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://about.mappls.com/api/img/icons/support.png)
[Support](https://about.mappls.com/contact/)
Need support? contact us!

<br></br>
<br></br>

[<p align="center"> <img src="https://about.mappls.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://about.mappls.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://about.mappls.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://about.mappls.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://about.mappls.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://about.mappls.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://about.mappls.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
