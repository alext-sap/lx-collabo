## Search REST API

The Search API returns a list of topics matching the specified search parameters.

***

### Request

**URI**: `https://help.sap.com/http.svc/search`

**HTTP Method: GET**

Permissions: Without authentication only public content \(state = PRODUCTION and read authorization for EVERYONE\) can be found.

***

#### Request Parameters

|Parameter|Required|Data Type|Description|Example|Parameter Type|
|---------|--------|---------|-----------|-------|--------------|
| **q** |Yes|String|Search term|data|Query string|
| **product** |No|String|Product as defined in the project map as metadata|SAP\_S4HANA\_CLOUD|Query string|
| **deliverable** |No|String|Deliverable LOIO \(output LOIO\)|610bd5556616b61ae10000000a44538d|Query string|
| **version** |No|String|Version as defined in the project map as metadata|1.2.4.0|Query string|
| **language** |No|String|Document language Default: en-US|en-US|Query string|
| **state** |No|String|Publishing status Default: PRODUCTION|DRAFT|Query string|
|**transtype**|No|String|Deliverable formatDefault: All transtypesPossible values: Standard \(includes html5.uacp, hp.sap, html5.lj\), HTML \(includes dhtml.sap, xhtml.sap, html5.sap, dhtml.sapcookbook\), PDF \(includes pdf.sap, pdf\), Others \(includes rtf, xhtml, chmhp.sap, eclipsehelp.sap, htmlhelp.sap, kwhtml.sap\)|html|Query string|
|**from**|No|String|Start value if paging is used for displaying search resultsDefault: 0|0|Query string|
|**to**|No|String|End value if paging is used for displaying search resultDefault: 30|20|Query string|

***

#### Request Example

- Default search for "database":

```
https://help.sap.com/http.svc/search?q=database
```

- Specific search in product SAP Predictive Analytics, format pdf, language English, version 3.2, and search term "predictive factory":

```
https://help.sap.com/http.svc/search?q=predictive+factory&product=SAP_PREDICTIVE_ANALYTICS&version=3.2&transtype=standard&language=en-US
```



### Response

***

#### Response Status and Error Codes

|Code|Reason|
|----|------|
|200|Data successfully returned|
|404|Content not found \(for example, due to invalid parameters\)|
|500|Internal server error|

***

#### Response Elements

The result is returned as JSON document as part of the response body. The table lists all elements. Depending on the search, some elements can be empty.

|Element|Description|Example|
|-------|-----------|-------|
|alternativeProductName|Alternative product name or acronym that has been defined for the product the topic belongs to.| |
|comments|Number of comments entered for the topic|0|
|date|Last publication date|2018-12-22|
|deliverableTitle|Title of the deliverable|Predictive Factory Online Help|
|description|Short description|An overview of model management.|
|documentType|The document type can be topic or product.|Topic|
|format|Format of the document. The format can be standard, HTML, PDF, or other \(see Request Parameters table\)|standard|
|language|Language of the topic|en-US|
|loio|Topic loio|c2f0326ebc89450f83f106529733d60e|
|mimeType|Mime type, for example, html, or PDF|text/html|
|path|Path is not used for search results. Therfore, it's always empty.|n/a|
|product|Name of the product the topic is part of|SAP Predictive Analytics|
|score|Ranking of the topic in the search results as calculated by Elasticsearch. The higher the score, the more relevant is the match.|546.82684|
|searchMetadata|The custom metadata values assigned to a topic. Only relevant when you search for content tagged with custom metadata.|courses|
|showLock|Whether the topic is part of a gated deliverable for which a lock is shown for not authorized \(or not logged in\) users.|false|
|size|Size of the content in bytes|1234|
|snippet|Excerpt of the topic containing the search term|About <b\>Predictive<\\/b\> <b\>Factory<\\/b\> ... <b\>Predictive<\\/b\> <b\>Factory<\\/b\> lets you create models and automate the management of <b\>predictive<\\/b\> models created in ...|
|state|Publishing status of the content|DRAFT|
|title|Title of the topic that is displayed in the search results|About Predictive Factory|
|transtype|Transtype \(output format\) of the topic|html5.uacp|
|url|URL to open the content|/viewer/DRAFT/41d1a6d4e7574e32b815f1cc87c00f42/3.2/en-US/c2f0326ebc89450f83f106529733d60e.html|
|version|Product version \(the version name\)|3.2|
|versionOom|Whether the product version the topic belongs to is out of mainstream maintenance|false|
|views|Not used in search results.|n/a|
|productId|Product ID of the product the topic belongs to|SAP\_PREDICTIVE\_ANALYTICS|
|versionId|Version ID of the product the topic belongs to|3.2|

***

#### Response Example

```
{
    "status": "OK",
    "data":     {
        "advanced": false,
        "query": "predictive factory",
        "maxResults": 0,
        "results":         [
                        {
                "alternativeProductName": "",
                "comments": "0",
                "date": "2018-12-22",
                "deliverableTitle": "Presentation of SAP BusinessObjects Predictive Analytics",
                "description": "",
                "documentType": "Topic",
                "format": "standard",
                "language": "en-US",
                "loio": "b69eccfb005d46bbb34dd709d97904b4",
                "mimeType": "text/html",
                "path": "",
                "product": "SAP Predictive Analytics",
                "score": "611.4173",
                "searchMetadata": {},
                "showLock": false,
                "size": "",
                "snippet": "<b>Predictive<\/b> <b>Factory<\/b> ... <b>Factory<\/b> is a thin-client, Web server-based application. ... <b>Predictive<\/b> <b>Factory<\/b> lets you automate the management of <b>predictive<\/b> models created in SAP BusinessObjects ... <b>Predictive<\/b> <b>Factory<\/b> brings new advantages to massive model automation: Segmented time series model management ... <b>Predictive<\/b> <b>Factory<\/b> is available only on Microsoft Windows, so if your modeling server is deployed on ... ",
                "state": "DRAFT",
                "title": "Predictive Factory",
                "transtype": "html5.uacp",
                "url": "/viewer/DRAFT/6887a1b4e5f348dc9d297b91701bda3d/3.2/en-US/b69eccfb005d46bbb34dd709d97904b4.html",
                "version": "3.2",
                "versionOom": false,
                "views": "0",
                "productId": "SAP_PREDICTIVE_ANALYTICS",
                "versionId": "3.2"
            },
                        {
                "alternativeProductName": "",
                "comments": "0",
                "date": "2018-12-22",
                "deliverableTitle": "Predictive Factory Installation and Administration Guide",
                "description": "",
                "documentType": "Topic",
                "format": "standard",
                "language": "en-US",
                "loio": "bb179b894484469095265fbef870436e",
                "mimeType": "text/html",
                "path": "",
                "product": "SAP Predictive Analytics",
                "score": "548.8205",
                "searchMetadata": {},
                "showLock": false,
                "size": "",
                "snippet": "Overview of <b>Predictive<\/b> <b>Factory<\/b> ... <b>Predictive<\/b> <b>Factory<\/b> is installed as part of an SAP BusinessObjects <b>Predictive<\/b> Analytics client-server ... The diagram shows <b>Predictive<\/b> <b>Factory<\/b> in the SAP BusinessObjects <b>Predictive<\/b> Analytics client-server landscape ... In <b>Predictive<\/b> <b>Factory<\/b>, you declare one or more modeling servers. ... <b>Predictive<\/b> Pipelines created with Expert Analytics can be imported in <b>Predictive<\/b> <b>Factory<\/b>. ... ",
                "state": "DRAFT",
                "title": "Overview of Predictive Factory",
                "transtype": "html5.uacp",
                "url": "/viewer/DRAFT/e3b264fbc92e4a10b21163d488966b0f/3.2/en-US/bb179b894484469095265fbef870436e.html",
                "version": "3.2",
                "versionOom": false,
                "views": "0",
                "productId": "SAP_PREDICTIVE_ANALYTICS",
                "versionId": "3.2"
            },
...
```

