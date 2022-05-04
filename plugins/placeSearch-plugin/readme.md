![Mappls APIs](https://about.mappls.com/images/mappls-b-logo.svg)


# Place Search Plugin for Mappls Web Maps

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

A simple plugin / widget to search for places powered by the best online maps from Mappls. The Place Search plugin for Mappls Web Map JS library is provided as a means to enable searching of Places on Mappls Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include Mappls Places JS in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to search for places directly with or without Mappls Maps visual interface.
2. A mappls.search() method to initiate search across all types places available on Mappls.
3. Ability to get information from Mappls Place Search plugin through a callback
4. Include the Place Search Plugin with or without an interactive Map component.


## Sample Implementation


Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placesearch/mappls-placesearch-plugin) for assistance to create a sample implementation with your own keys. 

For detailed understanding of the plugin, Let’s get started!


## Plugin's Configurations

Adding the Nearby Search plugin in the script

```js
<script src="https://apis.mappls.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins?v=3.0&libraries=search"></script>
```

### 1. Add the Place Search plugin

```js
      var placeOptions={
        location:[28.61, 77.23]};
        
    this.pluginObj.search("agra",placeOptions,callback);

    function callback(e: any)
    {    
        console.log(e);}
    }
```

#### Mandatory Parameters
1. `inputQuery`: The string which will be passed as input query to the search engine.

#### Optional Parameters
1. `Place Options`: Optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `pod`: Place type which you want to restrict the results by. e.g. `pod:'city'`. Valid values are: 
        - SLC (sub locality)
        - LC (locality)
        - CITY
        - VLG (village)
        - SDIST (sub district)
        - DIST (district)
        - STATE
        - SSLC (sub sub locality)
    - `filter`: a parameter to restrict results by. e.g. `filter:'cop:9qgxam'`
        - Can be used to filter results by PIN code. e.g. `pin:110055`
        - Can be used to filter results by eLoc. e.g. `cop:9qgxam`
        - Can be used to filter results by view bound. e.g. `filter=bounds:28.598882,77.212407;28.467375,77.353513`
    - `bridge`: initiates a bridge to be created to provide applicable nearby API searches. Involves using Nearby Search Plugin in conjunction with Place Search Plugin.
    - `hyperLocal`:This parameter lets the search give results that are hyper-localized to the reference location passed in the location parameter. This means that nearby                          results are given higher ranking than results far from the reference location. Highly prominent results will still appear in the search results, however theu                    will be lower in the list of results. This parameter will work ONLY in conjunction with the location parameter.
    - `tokenizeAddress`: boolean value used to return address tokens from the searched places from Mappls Search APIs. e.g. `tokenizeAddress:true`
    - `distance`: boolean value used to show aerial distance from location passed in `location`. of the searched place in results listing e.g. `distance:true`
    - `geolocation` : boolean value used to enable or disable current location selection . Default is true.
    - `width`: width of the suggested div. e.g. `width:300`
    - `height`: height of the suggested div. e.g `height:300`
    - `clearButton` : clear the value of input box. Default is true.
2. `callback`: callback to get results/error after call or selection.
3. `blank_callback` : callback when user clicks the cross button or erase the value of input box.

<br>

### 2. Calling Mappls Place Search for programmatically fixed text

Following is an example of calling Mappls.search() method programmatically for a fixed text rather than depending on a UI driven approach: 

```js
/*CALL for fix text - LIKE THIS*/
    new mappls.search("agra",placeOptions,callback);
```

### Other Methods

**setToken("token")** - This method is used when you receive a callback of token error. To set new token following method should be refered.

For Eg: if the users receives an error in callback like {error: "error-Passport invalid-Passport seems to be invalid or not active anymore-responsecode:401"}, 
use

```js
mappls.setToken();
``` 
If this returns true, then the token is placed successfuly, otherwise token is not valid.



That's All ! Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placesearch/mappls-placesearch-plugin) for assistance to create a sample implementation with your own keys. 


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

