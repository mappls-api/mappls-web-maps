[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Mappls Route Events Summary Plugin 

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (https://apis.mappls.com/console/) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Introduction

This plugin, offered by MapmyIndia Places & Directions SDK for Web, with the help MapmyIndia Rest API response dependency, provide the route events for the selected route.

This feature is also available inbuilt with MapmyIndia Direction Plugin. For details, please contact apisupport@mapmyindia.com.

## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-event-alongtheroute-direction-plugin)

## Implementation
```js
let routeOptions = {
                      map:this.mapObject,
                      routeId:"2959a08b-c9d1-11ec-8ea8-357ba8c4c378_Chrome:1010495141",
                      index:0
                  }
                  this.mapplsPluginObject.routeSummary(routeOptions,callback_method );
                  function callback_method(data: any){
                     console.log(data);
                 }
```

## Properties

### Mandatory Parameters

  - `map`(object): vector map or raster map object from respective MapmyIndia Map SDKs.
  - `routeId` (String) : routeId, Provide routeId if users needs to get all routes reports summary.

### Optional Parameters

 - `index` (String) : routeIdx, Provide routeIdx if user needs routes reports for a selected route only Otherwise returns events for all suggested routes.
 - `nodeId` (String) : nodeId, nodeId of the Route.
 - `categories` (String) : Optional, categories (comma(,) separated String).
 - `isGroup` (Integer) : sGroup, Set to 1, if user needs parentCategory wise grouped data.


<br>
That's All !

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
