## Implementing the Search JavaScript API

The Search API has been implemented as a JavaScript function, which allows you to easily integrate it into an HTML page.

1.  Download the JavaScript file `uacpsearchapi.js` from [https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/uacpsearchapi.js](https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/uacpsearchapi.js) and reference it from your html page.

2.  Add the following to your html page:

    To initialize the search API:

    > Note:
    > ```
    > var searchApi = new SearchApi();
    > ```
    > 
    > 

    To set the search parameters:

    > Note:
    > ```
    > var params =  searchApi.getDefaultParameters(); 
    > 								27 				params.q = `searchTerm`; 
    > 								28 				params.deliverable = "`loio`"; 
    > 								29 				params.version = "`version`"; 
    > 								30 				searchApi.setParameters(params);
    > ```
    > 
    > 

    > Note:
    > You must at least specify the search term, the other parameters are optional. For the deliverable parameter, enter the loio without the prefix *loio*.
    > 
    > 

    To request data via ajax call from server:

    > Note:
    > ```
    > searchApi.searchContent(onSearchResultRetrieved,onError);
    > ```
    > 
    > 


***

In this example, the parameters have been adapted to search in the SAP Medical Research Insights application help, version 2.0.

Source code: [https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/search.html](https://github.wdf.sap.corp/D032443/dkom2017/blob/gh-pages/search.html)

Demo: [https://github.wdf.sap.corp/pages/d032443/dkom2017/search.html](https://github.wdf.sap.corp/pages/d032443/dkom2017/search.html)

