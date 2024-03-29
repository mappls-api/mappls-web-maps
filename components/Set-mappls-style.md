[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)

# [Set Mappls style](#Set-MapplsMaps-style)

Mappls offers a range of preset styles to rendering the map. The user has to retrieve a list of styles for a specific account. 
The listing api would help in rendering specific style as well as facilitate the switching of style themes. 

From the below reference code it would become quite clear that user has to specify style names and not URLs to use them. 

You can get your api key to be used in this document here: [https://apis.mappls.com/console/](https://apis.mappls.com/console/)

A default style is set for all account users to start with. 
To know more about available styles, kindly contact apisupport@mapmyindia.com

To have a look at the refer
Live Demo: https://www.mapmyindia.com/api/advanced-maps/WebSDK-LiveDemo/map_style

React JS Components Live Demo : [CodeSandbox](https://codesandbox.io/p/sandbox/mappls-set-style-zmkzr4?file=%2Fsrc%2FApp.js)

**Angular Implementation:**

```js
import { Component, OnInit } from  '@angular/core';
import { mappls } from  'mappls-web-maps'

@Component({
selector:  'app-root',
template  :  '<div  id="map"  style="width: 99%; height: 99vh; background-color: white;"></div>',
styleUrls: ['./app.component.css']
})
export  class  AppComponent  implements  OnInit {
mapObject:  any;
mapplsClassObject =  new  mappls();

polylineObj : any;
mapProps = { center: [28.6330, 77.2194], traffic:  false, zoom:  4, geolocation:  false, clickableIcons:  false }

    
      ngOnInit() {

            this.mapplsClassObject.initialize("access_token",()=>{
                  this.mapObject  =  this.mapplsClassObject.Map({id:  "map", properties:  this.mapProps});
      
                  //load map layers/components after map load, inside this callback (Recommended)
                  this.mapObject.on("load", ()=>{
                  // Activites after mapload

                  this.componentAfterMapLoad();
                  
                  })
      
                  });

      }// ngoninit

                  componentAfterMapLoad()
                  {
                        this.mapplsClassObject.setStyle('standard-hybrid')
                  }

}
```
**React JS Implementation:**

```JS
import { mappls } from "mappls-web-maps";
import { useEffect, useRef, useState } from "react";

const mapplsClassObject = new mappls();

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
          center: [28.529467, 77.22315],
          zoom: 15,
        },
      });
      map.current.on("load", () => {
        setIsMapLoaded(true);
        mapplsClassObject.setStyle("standard-hybrid");
      });
    });
  }, []);

  return (
    <div
      id="map"
      style={{ width: "100%", height: "99vh", display: "inline-block" }}
    >
      {isMapLoaded}
    </div>
  );
};
export default App;

```


That's all!

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
