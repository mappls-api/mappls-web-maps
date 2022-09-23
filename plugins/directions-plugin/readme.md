[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)

# Direction Plugin for Mappls Web Maps

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.


## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 3.0 | 03 May 2022 | Mappls API Team ([MS](https://github.com/mamtasharma117)) |


## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Direction Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-direction-plugin)

## Introduction

This plugin, offered by Mappls Places & Directions SDK for Web, uses integrated places searches for directions for several modes of transportation, including driving, biking and walking.

The plugin offers the following basic functionalities:

1. Integrated support of Mappls(MapmyIndia) Place search for searching locations of origin, destinations and via points.
2. It allows to use origin and destinations in Mappls's digital address (semicolon separated) eLoc or WGS 84 geographical coordinates both.
3.  The ability to set the vehicle profile like driving, biking,trucking and walking.
4. Easily set the resource for traffic and ETA information.


For details, please contact apisupport@mappls.com.

## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-direction-plugin)


## Add the Direction plugin


```js
var direction_option = 
{
    Resource: 'route_eta',
    annotations:"nodes,congestion",
    map:this.mapObject,
    start:"28.545,77.545",
    end:
        {
            label:'India Gate, Delhi',
            geoposition:"1T182A"
        },
}
this.mapplsPluginObject.direction(direction_option, callback_method );
function callback_method(data: any)
    {
        console.log(data);
    }
```

## Properties

### Mandatory

1.  `map`(object): vector map or raster map object from respective Mappls Map SDKs.


### Optional Parameters

1. `start` (string): Mappls Pin(Eloc) or lat,long.
2. `end` (string): Mappls Pin(Eloc) or lat,long.
3. `resource` (string): Default is `route_adv` and can be changed to `route_eta` or `route_traffic` as per requirement.
4. `profile` (string): Default `driving` for four wheelers and can be changed to `biking` and `trucking` for two wheelers and heavy vehicles respectively.
5. `rtype` (boolean): type of route required for navigation, where values mean:
   - `0`: optimal (default)
   - `1`: shortest (it will calculate route by excluding access penalties like private roads, etc.)
6. `bearings`(integer): Limits the search to segments with given bearing in degrees. The referencing will be to the true north and in clockwise direction. (shall be part of premium offering)
7.  `alternatives`: Search for alternative routes. Passing a number: e.g. alternatives=n searches for up to n alternative routes. Please note that even if alternative routes are requested, a result cannot be guaranteed.
8.  `radiuses`: Limits the search to given radius in meters. For all way-points including start and end points. {radius};{radius}[;{radius} ...]. (shall be part of premium offering).
9. `steps`(boolean): Return route steps for each route leg. Possible values are true/false. By default it will be used as true. <Recommended=false; unless otherwise recommended by Mappls>
10. `stepPopup`: Possible values are true/false //By default false. If set true, steps written in popups will be shown.
11. `stepIcon`: Possible values are true/false //By default true. If set true, step icon will be visible.
12.  `exclude`(string): Additive list of road classes to avoid, order does not matter. Possible values are toll, motorway & ferry. Multiple values can be selected.
13. `start_icon` (string): To set the icon for start point.
    - Example: 
        ```js
        start_icon: {
            url: '2.png',
            width: 30, //optional
            height: 40 //optional
        }
        ```
        OR 
         ```js
         start_icon: {
            html: " < div > < img src = 'pin.png' > < /div>",
            width: 30, //optional
            height: 40, //optional
            offset:[20,40] //optional

        }
        ```
   
14. `end icon` (string) : To set the icon for end point.
15. `iconPopup` : Possible values are true/false. Sets popup for start, via and end icons. //By default true. 
16. `via`: (object) : To add a geo positions between start and end points.
    - Example: For single via Point
        ```js
        via: {
            label: 'mathura', //optional
            geoposition: "28.544, 77.4541"
        }
        ```
    - Example: For multiple via Points, user must pass the via points as array
        ```js
        via:
        [
            {
                label:'mathura',
                geoposition:"28.544,77.4541"
            },
            {
                label:'Koshi',
                geoposition:"28.144,77.4541"}],
        ```
17. `via_icon` (object): To set the icon for via points,
     - Example: 
        ```js
        via_icon:
        {
            url:'1.png',
            width:20,
            height:40
        }
        ``` 
        OR

        ```js
        via_icon:
        {
            html: <div> <img src = 'pin.png' > 1</div>, 
            width: 20,
            height: 40
        }
        ```
18. `fitbounds`: (boolean). Used to fit the route to in map view bound. Default is true.
19. `search` : Referred to the intergarated Mappls Search. Default remains true.
20. `divId`: The HTML where developer wishes results to be displayed.
21. `divWidth`: (in pixels) For customizing or improving results display UI.
22. `autoSubmit` : Property that will be called when user directly want to display the results. Default remains true.
23. `geolocation`: boolean value used to enable or disable current location selection . Default is true.
24. `maxVia`: Property that helps to limit the number of viapoints in any route. maximum Value  up to 98.
25. `searchChars` : number of characters required to start search. ie searchChars:2
26. `pod`: Place type which you want to restrict the results by. e.g. `pod:'city'`. Valid values are: 
    - SLC (sub locality)
    - LC (locality)
    - CITY
    - VLG (village)
    - SDIST (sub district)
    - DIST (district)
    - STATE
    - SSLC (sub sub locality)
    - POI (place of interest)
27. `distance`: boolean value used to show aerial distance from location passed in `location`. of the searched place in results listing e.g. `distance:true`
28. `hyperLocal`: This parameter lets the search give results that are hyper-localized to the reference location passed in the location parameter. This means that nearby results are given higher ranking than results far from the reference location. Highly prominent results will still appear in the search results, however they will be lower in the list of results. This parameter will work ONLY in conjunction with the location parameter.
29. `location`: location coordinates which will be used as radial bias search (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
30. `routeColor` : To configure the route colors displayed on the map. The colors will be applied in order of the route suggested. Will accept rgb, Hex code as well as color names.For Eg: If only one color is suggested then the most prior route color would be changed and rest routes will be shown in default colors. User can configure as many colors as per suggestions.
31. `strokeWidth` : To assign width of the route.The width will be applied in order of the route suggested. Default value is 4.For Eg: If only one width is suggested then the most prior route width would be changed and rest routes will be shown in default width. User can configure as many widths as per suggestions.
32.  `borderColor` : To assign color to the outline of the route.The colors will be applied in order of the route suggested. Will accept rgb, Hex code as well as color names.For Eg: If only one color is suggested then the most prior route color would be changed and rest routes will be shown in default color. User can configure as many colors as per suggestions.
33. `activeColor` : To configure the color of Active Route. Please note If `routeColor` is assigned then `activeColor` will hide the first suggested route.Will accept rgb, Hex code as well as color names.
34. `activeStrokeWidth` : To assign width of the route. Default value is 7.
35. `callback`: (function). To get callback data after route plotted.

## Additional Parameter - alongTheRoute
 
1. `alongTheRoute` : _true/false_. Default is false.
    
    To access this parameter , please contact [API Support](mailto:apisupport@mappls.com)
    This parameter takes the encoded route along which POIs will be searched. 
    
    This parameter is further having many configurable options listed below.

    - `buffer`: 200, _// Buffer of the road. Minimum value is 25m, maximum is 1000m and default is 25m_
    - `sort`: false, _//default is true_
    - `category`:  
        - `catCode`: 'FINATM', _//The POI category code to be searched. Only one category input supported by default_
        - `icon`: "icon image path
        " _//absolute path of the desired image_
        - `width`:  '30px' _//width of the icon image_
        - `height`: '30px' _//height of the icon image_
        - `label`: 'Restaurants' _the name  user puts to show the category. For Eg: "Restaurants"_

    - `page`: 1,  _// Used for pagination, Default is 1_
    - `poicallback`: to get data of alongtheroute pois.

 Refer to the Code Snippet if the you need to configure the default options.
 
 ```js
    alongTheRoute: 
        {
            options: 
                {
                    "page": 1,
                    "buffer": 1000,
                    "sort": false
                },
            category: 
                [
                    { 
                        catCode: 'FINATM', 
                        icon: "custom icon url", 
                        width: '30px', 
                        height: '30px',
                        label:'ATM'
                    },
                    { 
                        catCode: 'HOTALL', 
                        icon: "custom icon url", 
                        width: '30px', 
                        height: '30px',
                        label:'Hotels'
                    }
                ],
            poicallback: function(data)
                { 
                    console.log(data);
                }
        }
 ```
 
 _*Advisory - Route length should not be more than 30 kms long for optimal behaviour_

## Additional Parameter - routeSummary

1.  `routeSummary` : _true/false_. Default is false. This feature allows to show the events reports along the route like road and safety, traffic conditions etc.    
To access this parameter , please contact [API Support](mailto:apisupport@mappls.com).

Refer to the Code Snippet if the you need to get the callback.
 
 ```js
    routeSummary:
        {
            summarycallback: function(data)
                {
                    console.log(data);
                }
        },
 ```


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
