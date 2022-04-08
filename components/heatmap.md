[![N|Solid](https://about.mappls.com/images/mappls-logo.svg)](https://www.mapmyindia.com/api/)  

# Mappls Web Maps - For Angular/ Ionic / Cordova

You can get your api key to be used in this document here: [https://www.mapmyindia.com/api/signup](https://www.mapmyindia.com/api/signup)  


#  Heatmap Layer


## Adding a Heatmap Overlay
  
```js
this.heatmapObject = this.mapplsClassObject.HeatmapLayer({
map:this.mapObject,
data:[ {lat:  28.550144, lng:  77.263927}, {lat:  28.549637, lng:  77.264144} ],
opacity:1,
radius:10,
maxIntensity:10,
fitbounds:true,
gradient: [ 'rgba(0, 255, 255, 0)', 'rgba(0, 255, 255, 1)' ]
})
});
```

Email us at [apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com)

![](https://www.mapmyindia.com/api/img/icons/stack-overflow.png)
[Stack Overflow](https://stackoverflow.com/questions/tagged/mapmyindia-api)
Ask a question under the mapmyindia-api

![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

![](https://www.mapmyindia.com/api/img/icons/blog.png)
[Blog](http://www.mapmyindia.com/blog/)
Read about the latest updates & customer stories


> © Copyright 2022 CE Info Systems Ltd. All Rights Reserved. | [Terms & Conditions](http://www.mapmyindia.com/api/terms-&-conditions)