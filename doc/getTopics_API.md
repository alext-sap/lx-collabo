## getTopics API

The getTopics API retrieves one or multiple topics from the SAP Help Portal based on metadata.

***

<a name="loio4434d3dfe0ed44d7968bd5341a4b8e9b__section_ggb_wz1_g4b"/>

### Usage

Topics can be tagged in the Ixiasoft CMS with custom \(or flexible\) metadata which are defined in a classification map. An example is the Fiori application id which is used by SAP CoPilot to identify topics relevant for a Fiori application. Another use case could be to identify topics tagged with specific error codes. When you call up the API with the metadata in the form of a key-value pair, the respective topics are returned, either with their content, or just the metadata.

It's also possible to extract only specific parts of a topic. The respective parts must carry and ID which starts with the prefix `ct_`. The UA developer assigns these IDs to the elements in the Ixisoft CMS, for example, `<p id="ct_feature_01"`. Only content which is tagged with such IDs is then extracted when you call up the getTopics API with the parameter `output=metadata`.

***

### Request

**URI:**`https://help.sap.com/http.svc/gettopics` 

**HTTP Method:****GET**

**Permissions:**All content you want to retrieve needs to be authorized for public access \(state = PRODUCTION and read authorization for EVERYONE\)

***

#### Request Parameters

|Parameter|Required|Data Type|Description|Example|Parameter Type|
|---------|--------|---------|-----------|-------|--------------|
|**<key\>=<value\>**|Yes|String|Flexible key value pair as defined in the DITA CMS|fiori-id=F0002|Query string|
|**product**|No|String|Product ID in UACP|SAP\_S4\_HANA|Query string|
| **deliverable** |No|String|Deliverable Loio \(Output ID\)|a14ec5921d4c420298b27a8cdd4e4abb|Query string|
| **version** |No|String|Version of the deliverable Instead of the version, you can also enter **latest** to get the results for the latest version.|1.0|Query string|
| **language** |No|String|Language of the document Default: en-US|en-US|Query string|
|**fallbackLanguage**|No|String|Fallback language, if the content is not found in the specified language.For example, if language=de-DE and fallbackLanguage=en-US, if no result is available in German, then the English result is returned.|en-US|Query string|
| **transtype** |No|String|Transtype \(output format\) of the deliverable Default: html5.uacp|dhtml.sap|Query string|
|state|No|String|Publication stateDefault: Production|Draft|Query string|
| **topic** |No|String|Topic loio|69c51e38264c4f169a76f7a115196d1|Query string|
|**nocontent**|No|String|If set to true, only metadata is returnedDefault: false|false|Query string|
| **display** |No|String|Defines the if the URL should be opened directly in the browser|browser|Query string|
|**output**|No|String|If output = metadata, then only content which carries an ID which starts with `ct_` is extracted from the topic.|metadata|Query string|

***

#### Request Example

URL only metadata: `[https://help.sap.com/http.svc/gettopics?sf-feature=virtual\_learning\_systems](https://help.sap.com/http.svc/gettopics?sf-feature=virtual_learning_systems)`

URL with content : `[https://help.sap.com/http.svc/gettopics?sf-feature=virtual\_learning\_systems&nocontent=false](https://help.sap.com/http.svc/gettopics?sf-feature=virtual_learning_systems&nocontent=false)`

URL that opens in the browser: `[https://help.sap.com/http.svc/gettopics?sf-check-id=PMFormTemplateRatingPermissionsCheck&display=browser](https://help.sap.com/http.svc/gettopics?sf-check-id=PMFormTemplateRatingPermissionsCheck&display=browser)`

URL that extracts specifically tagedd parts of a topic: `[http://help.sap.com/gettopics?output=metadata&nocontent=false&language=en-US&slm-asset-id=113660a0-b4f5-4500-a9ce-f51b671ddb9a](http://help.sap.com/gettopics?output=metadata&nocontent=false&language=en-US&slm-asset-id=113660a0-b4f5-4500-a9ce-f51b671ddb9a)` 

***

### Response

***

#### Response Status and Error Codes

|Code|Reason|
|----|------|
|200|Data successfully returned|
|403|Not authorized|
|404|Content not found|
|500|Internal server error|

***

#### Response Elements

The result is returned as JSON document. The table list all parameters. Depending on the type of document some elements can be empty.

|Element|Description|Example|
|-------|-----------|-------|
|date|Last publication date|2017-02-05|
|description|Short description or snippet of the topic|The Max DB .....|
|documentType|Document type \(always topic\)|Topic|
|format|Format of the document. Allowed values are: Standard \(html5, uacp\), HTML, PDF, Others \(rtf, xhtml\)|standard|
|lastModifiedById|SAP user ID|i024155@global.corp.sap|
|lastModifiedDate|Date and time format: YYYY-MM-DD HH:MM:SS HH:MM:SS is optional|2018-03-02|
|mimeType|Mime type, for example, html, or PDF|text/html|
|product|Product the topic is part of|SAP NetWeaver|
|size|Size of the content in bytes|1234|
|state|Publishing status of the content|DRAFT|
|title|Title of the topic that is displayed in the search results|Topic with SearchMetadata==F0002|
|transtype|Transtype \(output format\) of the topic|html5.uacp|
|url|URL to open the content|/viewer/e7b01d4b75b14de7b156fe2b8881a71b/2016/en-US/6761bd82a54947d98b60631ff29ccc39.html|
|version|Product version derived from deliverable|7.5 SPS02|
|content|Content from uacp that can be displayed|<html\><title\>Search Metadata Example.....</html\>|

***

#### Response Example

```
{
    "status": "OK",
    "data": {"content":     {
        "content": "<!DOCTYPE html  SYSTEM \"about:legacy-compat\">\<html lang=\"en-us\" dir=\"ltr\">   <head> ....<\/html>",
        "date": "2016-03-10",
        "description": "The error messages generated by the SAP DITA Framework are seen in the\n\t\tBuild Dashboard's Log Analyzer. They contain a message ID, severity level, and message text,\n\t\tfollowing DITA-OT conventions. This topic lists each error message type and provides\n\t\tadditional information to help understand and resolve the error condition.",
        "documentType": "Topic",
        "format": "standard",
        "mimeType": "text/html",
        "product": "dita_output_validation_uacp",
        "size": "0",
        "state": "DRAFT",
        "title": "SAP DITA Framework Error Messages",
        "transtype": "html5.uacp",
        "url": "/viewer/#/DRAFT/e3a1c96e2b8145298541ce21b0f5c983/1/en-US/3f1a18dc1a4143b884020af3483d7359.html",
        "version": "1"
    }}
}
```

**Related information**  


[Creating New Search Metadata](https://help.sap.com/viewer/DRAFT/bba968de69fc4814b97a0da987913be1/1/en-US/f9e759e6009449bcb1a8bbbc7e2f0dd7.html)

[How Is Custom Metadata Used by UACP getTopics API?](https://help.sap.com/viewer/DRAFT/bba968de69fc4814b97a0da987913be1/1/en-US/b17cc24a9d1c42e395bb6ef6f3598a4f.html)

