## Search API: Search with Custom Metadata

**–WORK IN PROGRESS---**You can search for topics which have been classified with custom metadata by adding the metadata as filter to the search query.

***

### Usage

In addition to the standard metadata, like product and language, authors can assign custom metadata to topics. This custom metadata is specific for the product or product area. When the custom metadata is added as filter to the search query, only topics which are tagged with this metadata are included in the search results.

***

### Request

**URI:** [https://help.sap.com/http.svc/elasticsearch](https://help.sap.com/http.svc/elasticsearch)

**HTTP Method:** POST

**Permissions:** Without authentication only public content \(state = PRODUCTION and read authorization for EVERYONE\) can be found.

***

#### Request Parameters

In addtion to the parameters based on the standard metadata \(see [Search REST API](Search_REST_API.md)\), you can use the following parameters:

|Parameter|Required|Data Type|Description|Parameter Type|
|---------|--------|---------|-----------|--------------|
|filter|No|String|Defines the metadata you want to use to filter the search results. Consists of a key-value pair. The key is the category name, and the value is the actual metadata value. You can specify multiple values for a key.|Body|
|searchMetadata|No|String|Defines which metadata values you want to see in the response. Doesn't affect what results are returned, only adds information to the existing results if the specified properties exist for the topics.|Body|
| | | | | |
| | | | | |

***

#### Request Body Example

```

						```

{
    "area":"content",
    "product":"SAP_SUCCESSFACTORS_LEARNING",
    "language":"en-US",
    "q":"learning",
    "filter":{
        "sf-feature":[
            "courses",
            "instructor_management"
        ]
    },
	"searchMetadata":["sf-feature"]
}
```


					
```

***

<a name="loiofd8ce73dec084eb397f4096e0c9b2976__section_pys_vts_hnb"/>

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

#### Response Body Example

```

					```

 {
    "status": "OK",
    "data": {
        "advanced": false,
        "query": "learning",
        "maxResults": 0,
        "results": [
            {
                "alternativeProductName": "",
                "comments": "0",
                "date": "2020-10-19",
                "deliverableTitle": "",
                "description": "Use folders to organize the online content of learning items (courses) in SAP SuccessFactors Learning.",
                "documentType": "Topic",
                "format": "standard",
                "language": "en-US",
                "loio": "fe2fdb2168ab4938ad6ab6c6d08d5c0e",
                "mimeType": "text/html",
                "path": "",
                "product": "SAP SuccessFactors Learning",
                "score": "190.95074",
                "searchMetadata": {
                    "sf-feature": [
                        "courses"
                    ]
                },
                "showLock": false,
                "size": "",
                "snippet": "Organizing Online <b>Learning</b> Content for a <b>Learning</b> Item Use folders to organize the online content of ... <b>learning</b> items (courses) in SAP SuccessFactors <b>Learning</b>. ... and opening the <b>learning</b> item. ... Go to SAP SuccessFactors <b>Learning</b> administration and then go to <b>Learning</b> Activities&nbsp;&nbsp;Items. ... Find and open the <b>learning</b> item. ... ",
                "state": "DRAFT",
                "title": "Organizing Online Learning Content for a Learning Item",
                "transtype": "html5.uacp",
                "url": "/viewer/DRAFT/89d2de1a0de943e6937589aa547d30de/2011/en-US/fe2fdb2168ab4938ad6ab6c6d08d5c0e.html",
                "version": "2H 2020",
                "versionOom": false,
                "views": "0",
                "productId": "SAP_SUCCESSFACTORS_LEARNING",
                "versionId": "2011"
            },
```


				
```

