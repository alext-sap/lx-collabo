## Content JavaScript API

The Content API has been implemented as a JavaScript function, which allows you to easily integrate it into an html page.

1.  Download the JavaScript file `uacpcontentapi.js` from [https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/uacpcontentapi.js](https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/uacpcontentapi.js) and reference it from your html page.

2.  Add the following to your html page:

    To initialize the content API:

    > Note:
    > ```
    > var contentApi = new ContentApi();
    > ```
    > 
    > 

    To create a request and retrieve content from the help portal:

    > Note:
    > ```
    > 
    > 21 		function displayAbout() { 
    > 22 			var params = this.contentApi.getDefaultParameters(); 
    > 23 			params.deliverable = "`loio`"; 
    > 24 			params.version = "`version number`"; 
    > 25 			params.topic = "`topic loio`"; 
    > 26 			params.transtype = "`output format`"; 
    > 27 			params.language="`locale`"; 
    > 28 			params.nocontent = `false` or `true`; 
    > 29 			 
    > 30 			// set the parameters to the content api for later requests 
    > 31 			this.contentApi.setParameters(params); 
    > 32 			contentApi.readContent(onContentRetrieved,onError); 
    > 33  
    > 34 			$("#results_display").html(""); 
    > 35 			$("#loading_animation").show(); 
    > 36 		}; 
    > 
    > ```
    > 
    > 

    > Note:
    > For the deliverable parameter and topic parameter, enter the loios without the prefix *loio*
    > 
    > 


***

This example displays content of the SAP Medical Research Insights application help, version 2.0.

Source code: [https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/contentapi.html](https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/contentapi.html)

Demo: [https://github.wdf.sap.corp/pages/d032443/dkom2017/contentapi.html](https://github.wdf.sap.corp/pages/d032443/dkom2017/contentapi.html)

