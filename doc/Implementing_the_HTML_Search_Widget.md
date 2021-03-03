## Implementing the HTML Search Widget

To implement the search widget, you need to add a few lines of code to your html page and to add some JavaScript files to your project.

1.  Download the following files from [https://github.wdf.sap.corp/D032443/UAWidgets/tree/gh-pages/searchwidget/js](https://github.wdf.sap.corp/D032443/UAWidgets/tree/gh-pages/searchwidget/js) and make them available to your project:

    -   `search_api.js`
    -   `search_client.js`
    -   `search_config_api.js`
    -   `search_config_widget.js`
    -   `default.css`
2.  In the header of your html page, reference the following scripts and stylesheets:

    > Note:
    > ```
    > <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css"> 
    > <link rel="stylesheet" href="css/default.css"> 
    > <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script> 
    > <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script> 
    > 
    > ```
    > 
    > 

3.  Link the JavaScript files you have downloaded:

    > Note:
    > ```
    > <script src="<path>/search_api.js"></script>
    > <script src="<path>/search_config_api.js"></script>
    > <script src="<path>/search_config_widget.js"></script>
    > <script src="<path>/search_client.js"></script>
    > 
    > 
    > ```
    > 
    > 

4.  Insert the search form:

    > Note:
    > ```
    > <div id="search-widget">
    >     <header>
    >         <h2 id="search-title">Search</h2>
    >     </header>
    >     <form onsubmit="return startSearch()">
    >         <div id="form-container" class="input-group">
    >             <input type="text" class="form-control" id="search-input" placeholder="Enter keywords">
    >             <span class="input-group-btn">
    >                 <button type="submit" id="search-button" class="btn btn-default" >
    >                     <span class="glyphicon glyphicon-search"></span>
    >                     <span class="searchbtn-text"></span>
    >                 </button>
    >             </span>
    >         </div>
    >     </form>
    >     <div id="results-display" class="">
    >     </div>
    >     <div id="pagination-container">
    >     </div>
    >     <div class="loader" id="loading-animation" style="display:none"></div>
    > </div>
    > 
    > ```
    > 
    > 

5.  Call up the `configureWidget` method:

    > Note:
    > ```
    > <script>searchConfigWidget.configureWidget();</script>
    > 
    > ```
    > 
    > 

6.  Define the search parameters deliverable loio, version, product, and language.You can either define them in the `search_config_api.js` file, or set the parameters in your html file, which allows for more flexibility.

    -   In the search\_config\_api.js, set the parameters using the the following coding:

        > Note:
        > ```
        > this.parameters = { 
        >         deliverable: "output loio", 
        >         version: "version number", 
        >         product: "product", 
        >         language: "locale"       
        >     }; 
        > 
        > ```
        > 
        > 

        All parameters are optional.

        Example

        ```
        
        								        ```
                this.parameters = { 
                		deliverable: "de8f93d628384b59a3b4b6d9edf4a95b",
                		version: "1611 500", 
                		product: "SAP_S4HANA_CLOUD",
                		language:"fr-FR"
                };
                ```
        
        
        							
        ```

    -   In your html page, use the following coding:

        ```
        
        								        ```
                searchConfigApi.parameters.deliverable = "output loio";
                searchConfigApi.parameters.version = "version number";
                searchConfigApi.parameters.product = "product";
                searchConfigApi.parameters.language = "locale";
                searchConfigApi.configureApi();
                
                ```
        
        
        							
        ```

7.  Optionally, you can also change the attributes of the widget itself. Again, you can do it in the JavaScript file \(`search_config_widget.js`\) or in your html file:

    -   In the search\_config\_widget.js, set the parameters using the the following coding:

        > Note:
        > ```
        > this.title = "Title of search widget";                    
        > 5     this.buttonText = "Text on search button, if empty only search icon is displayed"
        > ";    // 
        > 6     this.inputPlaceholder = "Text in search field";   
        > 7     this.stylesheet = "Stylesheet for widget";   
        > 8     this.maxResults = Number of results per page;       
        > 9     this.descriptionOn = If true, then the short description of the found topics will be displayed;  
        > 
        > ```
        > 
        > 

        Example:

        ```
        
        								        ```
                 this.title = "Search";                      
                5     this.buttonText = "Go!";                       
                6     this.inputPlaceholder = "Enter keywords";   
                7     this.stylesheet = "css/default.css";                       
                8     this.maxResults = 8;                        
                9     this.descriptionOn = false;  
                
                ```
        
        
        							
        ```

    -   In your html page, use the following coding:

        ```
        
        								        ```
                
                searchConfigWidget.title = "Title of search widget";
                searchConfigWidget.buttonText = "Text on search button, if empty only search icon is displayed";
                searchConfigWidget.inputPlaceholder = "Text in search field"; 
                searchConfigWidget.stylesheet "Stylesheet for widget";
                searchConfigWidget.maxResults = 6;
                searchConfigWidget.descriptionOn = true;
                searchConfigWidget.configureWidget();
                
                ```
        
        
        							
        ```


