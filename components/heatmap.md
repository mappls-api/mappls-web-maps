[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api) 

# Mappls Web Maps - For Angular/ Ionic / Cordova

###  Heatmap Layer

A heatmap layer is a visualization technique used in data analysis and mapping to represent the intensity of data values in a two-dimensional space. It is commonly used to visualize the distribution of data points and highlight areas with higher or lower concentrations.
This layer assigns colors to different regions based on the intensity of the underlying data. You start with a set of data points, each associated with a specific location (latitude and longitude in the case of maps).
Each data point has a value representing the intensity or magnitude of the phenomenon you are visualizing (e.g., temperature, population density, etc.).Define a color scale that represents the range of values in your data. For example, you might use a gradient from cool to warm colors.For each data point, determine its position on the color scale based on its value. The color assigned to the point corresponds to its position on the scale. Lastly render the layer on the map using the below mwnetioned methods.
You can get your api key to be used in this document here: [Mappls Console](https://outpost.mappls.com/api/sso/login.jsp)

React JS Implementation Live Video : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-heatmap-z75nlv?file=%2Fsrc%2FApp.js%3A1%2C1-66%2C1)

#### Adding a Heatmap Overlay
  
```js
this.heatmapObject = this.mapplsClassObject.HeatmapLayer(
    {
        map: this.mapObject,
        data: [ 
            {
                lat:  28.550144, 
                lng:  77.263927
            },
            {
                lat:  28.549637, 
                lng:  77.264144
            }],
        opacity:1,
        radius:10,
        maxIntensity:10,
        fitbounds:true,
        gradient: [ 'rgba(0, 255, 255, 0)', 'rgba(0, 255, 255, 1)' ]
    })
});
```
#### Removing a Heatmap Overlay

```js
mapplsClassObject.removeLayer({
    map: mapObject,
    layer: heatmapObject,
  });
```
#### **React JS Implementation**

```js
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

const HeatmapComponent = ({ map }) => {
  const HeatmapRef = useRef(null);

  useEffect(() => {
    if (HeatmapRef.current) {
      mapplsClassObject.removeLayer({ map: map, layer: HeatmapRef.current });
    }
    HeatmapRef.current = mapplsClassObject.HeatmapLayer({
      map: map,
      data: [
        {
          lat: 28.550144,
          lng: 77.263927,
        },
        {
          lat: 28.549637,
          lng: 77.264144,
        },
      ],
      opacity: 1,
      radius: 10,
      maxIntensity: 10,
      fitbounds: true,
      gradient: ["rgba(0, 0, 255, 0)", "rgba(0, 0, 255, 1)"],
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
          center: [28.633, 77.2194],
          zoom: 4,
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
      {isMapLoaded && <HeatmapComponent map={map.current} />}
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
