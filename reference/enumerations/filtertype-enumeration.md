
# FilterType enumeration (JavaScript API for Office)
Specifies whether filtering from the host application is applied when the data is retrieved.

|||
|:-----|:-----|
|**Hosts:**|Excel, Project, Word|
|**[Last changed](#bk_history) in**|1.1|
[See all support details](#bk_support)

```
Office.FilterType
```


## Members


**Values**


|**Enumeration**|**Value**|**Description**|
|:-----|:-----|:-----|
|Office.FilterType.All|"all"|Return all data (not filtered by the host application).|
|Office.FilterType.OnlyVisible|"onlyVisible"|Return only the visible data (as filtered by the host application).|

## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this enumeration is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this enumeration.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


**Supported hosts, by platform**


||**Office for Windows desktop**|**Office Online(in browser)**|**Office for iPad**|
|:-----|:-----|:-----|:-----|
|**Excel**|Y|Y|Y|
|**Project**|Y|||
|**Word**|Y||Y|

|||
|:-----|:-----|
|**Add-in types**|Content, task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.1|Added support for Excel and Word in Office for iPad.|
|1.0|Introduced|
