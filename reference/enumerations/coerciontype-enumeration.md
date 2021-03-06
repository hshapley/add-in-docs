
# CoercionType enumeration (JavaScript API for Office)
Specifies how to coerce data returned or set by the invoked method.

|||
|:-----|:-----|
|**Hosts:**|Access, Excel, Outlook, PowerPoint, Project, Word|
|**[Last changed](#bk_history) in Mailbox**|1.1|
[See all support details](#bk_support)

```
Office.CoercionType
```

[![Try out this call in the interactive API Tutorial for Excel](../../images/819b84bf-151c-4a12-80c3-d6f8d7c03251.png)](http://officeapitutorial.azurewebsites.net/Redirect.mdl?scenario=Write+and+Read+Text&amp;task=readSelectedDataText)

## Members


**Values**


|**Enumeration**|**Value**|**Description**|
|:-----|:-----|:-----|
|Office.CoercionType.Html|"html"|Return or set data as HTML.
 **Note**  Only applies to data in add-ins for Word and Outlook add-ins for Outlook (compose mode).

|
|Office.CoercionType.Matrix|"matrix"|Return or set data as tabular data with no headers. Data is returned or set as an array of arrays containing one-dimensional runs of characters. For example, three rows of  **string** values in two columns would be: `[["R1C1", "R1C2"], ["R2C1", "R2C2"], ["R3C1", "R3C2"]]`.
 **Note**  Only applies to data in Excel and Word.

|
|Office.CoercionType.Ooxml|"ooxml"|Return or set data as Office Open XML.
 **Note**  Only applies to data in Word.

|
|Office.CoercionType.SlideRange|"slideRange"|Return a JSON object that contains an array of the ids, titles, and indexes of the selected slides.For example,  `{"slides":[{"id":257,"title":"Slide 2","index":2},{"id":256,"title":"Slide 1","index":1}]}` for a selection of two slides.
 **Note**  Only applies to data in PowerPoint when calling the [Document.getSelectedData](../reference/shared/document/getselecteddataasync-method.md) method to get the current slide or selected range of slides.

|
|Office.CoercionType.Table|"table"|Return or set data as tabular data with optional headers. Data is returned or set as an array of arrays with optional headers.
 **Note**  Only applies to data in Access, Excel and Word.

|
|Office.CoercionType.Text|"text"|Return or set data as text ( **string**).Data is returned or set as a one-dimensional run of characters.|
|Office.CoercionType.Image|"image"|Data is returned or set as an image stream.
 **Note**  Only applies to data in Excel, Word and PowerPoint.

|
PowerPoint supports only  **Office.CoercionType.Text**,  **Office.CoercionType.Image**, and  **Office.CoercionType.SlideRange**.

Project supports only  **Office.CoercionType.Text**.


## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this enumeration is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this enumeration.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


**Supported hosts, by platform**


||**Office for Windows desktop**|**Office Online(in browser)**|**Office for iPad**|**OWA for Devices**|**Office for Mac**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Access**|Y|||||
|**Excel**|Y|Y|Y|||
|**Outlook**|Y|Y||Y|Y|
|**PowerPoint**|Y|Y|Y|||
|**Project**|Y|||||
|**Word**|Y|Y|Y|||

|||
|:-----|:-----|
|**Add-in types**|Content, Outlook (compose mode), task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.1|Added support for Word Online.|
|1.1|Added support for Excel, PowerPoint, and Word in Office for iPad.|
|1.1|Added support for add-ins for Access.|
|1.1|Added support for [compose mode Outlook add-ins](http://msdn.microsoft.com/library/e4126e58-4ddc-4891-9f19-aa6c1a258027%28Office.15%29.aspx).|
|1.0|Introduced|
