## Checking Stored Configuration

You can check which parameter configuration has been stored with a specific profile ID.

***

Permissions?

1.  Call up [https://help.sap.com/http.svc/predefined\_profiles](https://help.sap.com/http.svc/predefined_profiles) with the GET method and with the profile ID as parameter.

    > Note:
    > [https://help.sap.com/http.svc/predefined\_profiles?profile=20000418](https://help.sap.com/http.svc/predefined_profiles?profile=20000418)
    > 
    > 

    ```
    
    						    ```
        {
            "status": "OK",
            "data":     {
                "profileId": 20000418,
                "profileSelection":         {
                    "product_area_code": "S4HC",
                    "/CPD/CA_CPD_SS_EMPSRCHBYFIELDS": "false",
                    "/CPD/CA_CPD_SS_EXTAPI_DEMAND": "true",
                    "/CPD/CA_CPD_SS_EXTAPI_SUPPLY": "true",
                    "/CPD/CA_CPD_SS_OTHRESOURCE": "true",
                    "/CPD/CA_CPD_SS_STAFFING_INSTRUCTION": "true",
                    "/CPD/CA_CPD_SS_STAFFING_INSTRUCTIONS": "true",
                    "/IWXBE/FT_TOPICCONSUMER": "false",
                    "/PLMI/CR_FM_ACM": "true",
        ......
        								}
        			}
        		}
        ```
    
    
    					
    ```


