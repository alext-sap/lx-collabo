## predefined\_profiles REST API

–- Work in progress –- This API stores a feature flag configuration on the UACP database and creates and returns a profile ID for it. With this profile ID, an application can then call up content from the UACP which is filtered according to the enabled feature flags.

***

<a name="loio6c6e2cf5a3004efd82821ee99f7a2592__section_bz1_qh1_5mb"/>

### Usage

This API can be used in a dynamic consumption scenario, where the user assistance content is filtered at consumption time so that it fits to the activated featues in the customer's tenant. In an application system, some features can be activated or not, according to the individual needs of the customers. Accordingly, they need the corresponding user assistance for the activated features.

To make this work, the user assistance developer needs to add feature flags to the application help, so that the content for a specific feature can be identified. The complete application help containing help for all features is then uploaded to the Help Portal.

The application system uses the predefined\_profiles API to sent the information which features are enabled to the Help Portal. The configuration is stored in the Help Portal database and UACP creates a profile ID for it. This profile ID is returned to the application system. When a user calls up the help from within the system, the profile ID is appended to this call \(*https://help.sap.com/viewer/<output ID\>/<version\>/<language\>/<topic loio\>.html?profile=<ID\>*\). The help is then filtered accordingly. The feature-flag-based filtering works for in-app help \(Web Assistant\) and html5.uacp output displayed in the Help Portal viewer.

***

<a name="loio6c6e2cf5a3004efd82821ee99f7a2592__section_pcs_hyz_tmb"/>

### Request

**URI:**For on-premise products, use [https://cp1canary.int.sap.eu2.hana.ondemand.com/dps/http.svc/predefined\_profiles](https://cp1canary.int.sap.eu2.hana.ondemand.com/dps/http.svc/predefined_profiles). It acts as a proxy, so the caller does not need to be logged in to the Help Portal. For cloud products, you can use [https://help.sap.com/dps/http.svc/predefined\_profiles](https://help.sap.com/dps/http.svc/predefined_profiles), if the application is already logged in with SAP Identity Service.

**HTTP Method:****POST**

**Permissions:**SAP employees can calll up the API.

***

#### Request Parameters

The parameters have to be added to the request body in the form of a JSON object.

|Parameter|Required|Data Type|Description|Example|Parameter Type|
|---------|--------|---------|-----------|-------|--------------|
|**product\_area\_code**|Yes|String|A unique code within SAP used amongst others as a name space to ensure the uniquness of the feature names.|S4H|Body|
|**feature\_name**|Yes|String|Feature flag name as used in the content and in the feature flag system. It's value can be true or false. You can enter as many key/value pairs as you need.|FIN\_PSM\_CO\_INTEGRATION|Body|

***

#### Request Body Example

```

						```
{
"product_area_code": "S4HC",
"/CPD/CA_CPD_SS_EMPSRCHBYFIELDS": "false",
"/CPD/CA_CPD_SS_EXTAPI_DEMAND": "true",
"/CPD/CA_CPD_SS_EXTAPI_SUPPLY": "true",
"/CPD/CA_CPD_SS_OTHRESOURCE": "true",
"/CPD/CA_CPD_SS_STAFFING_INSTRUCTION": "true",
"/CPD/CA_CPD_SS_STAFFING_INSTRUCTIONS": "true",
"/IWXBE/FT_TOPICCONSUMER": "false"
}
```


					
```

***

<a name="loio6c6e2cf5a3004efd82821ee99f7a2592__section_cty_ff1_5mb"/>

### Response

***

#### Response Status and Error Codes

|Code|Reason|
|----|------|
|200|Profile ID successfully returned|

***

#### Response Body Example

```

					```
{
    "status": "OK",
    "data":     {
        "profileId": 20000418}
 }
```


				
```

**Related information**  


[Managing Content with Feature Flags](https://help.sap.com/viewer/DRAFT/bba968de69fc4814b97a0da987913be1/1/en-US/4002f48917aa41a1b19b4b890138a6de.html)

