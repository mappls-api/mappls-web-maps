![Mappls APIs](https://about.mappls.com/images/mappls-b-logo.svg)


# Place Details Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (https://apis.mappls.com/console/) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of Mappls APIs. 


## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 3.0 | 22 April 2022 | Mappls API Team ([MS](https://github.com/mamtasharma117)) |



## Introduction

A simple plugin / widget to render details of a particular place. The Place Details plugin for MapmyIndia Web Map JS library is provided as a means to enable rendering of MapmyIndia Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web map implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to render places directly on map with reference to the provided eLoc(s).
2. A getPinDetails() method to fetch the details of a place.
3. Customizable markers
4. Remove markers from map.

## Sample Implementation


Visit the [samples](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin) for assistance to create a sample implementation with your own keys. 

For detailed understanding, Let’s get started!

## Add the Place Details plugin

```js
    var elocObj =  this.mapplsPluginObject.getPinDetails({ map: this.mapObject, pin:"mmi000"}, callback_method );
                  function callback_method(data: any){
                     console.log(data);
                 }
```

#### Mandatory Parameters
1. `pin`: The pin (Mappls Pin/Eloc) whose details are required.
2. `callback`: to return data to a specified callback method.


#### Optional Parameters
1. `map`: Map Object
2. `icon`: custom icon url.
3. `divId`: The div to put the result in.
4. `markerPopup` (boolean): to show pop-ups on marker click. Default is true.(example: `markerPopup:true`)
5. `popupHtml`: to show html pop up on marker click. User should define values to be shown while using this parameter.(example: `obj.setPopup({content:"<h1>Hello MapmyIndia</h1>"})`)
6. `fitbounds` (boolean): To show all rendered eLoc(s) in a single view bound. (example: `fitbounds:true`)
7. `fitboundOptions` : padding in fitbounds, if any. (Example: `{ padding:50,maxZoom:18}`)
8. `infoDiv` (boolean): To render html div on map or not. Default is true. (example: `infoDiv:true`)
9. `click_callback`: method to call on click of callback. 

### 3. Method to remove the markers with callback populated by Place Details Plugin

```js
elocObj.remove();
```

### 4. Method to set up the div content for populating details from getPinDetails() plugin

```js
elocObj.setDivContent(“Div html);
```
### 5. Method to set up the pop up content on marker as html.
For Eg:

```js
elocObj.setPopup({content:"<h1>Hello Mappls</h1>"});
```


That's All ! Visit the [samples](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin) for assistance to create a sample implementation with your own keys.



For any queries and support, please contact: 

<img src="https://cdn.mapmyindia.com/mappls_web/maps_widget_v2/images/mappls.svg?service=google_gsuite"  width="500" height="200" />

Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mapmyindia-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](http://www.mapmyindia.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/MapmyIndia)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/MapmyIndia)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/MapmyIndia)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mapmyindia)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/user/MapmyIndia/)




<div align="center">© Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://www.mapmyindia.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://www.mapmyindia.com/about/privacy-policy">Privacy Policy</a> | <a href="https://www.mapmyindia.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://www.mapmyindia.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://www.mapmyindia.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
