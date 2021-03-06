
# File object (JavaScript API for Office)
Represents the document file associated with an Office Add-in.

|||
|:-----|:-----|
|**Hosts:**|PowerPoint, Word|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|File|
|**[Last changed](#bk_history) in**|1.1|
[See all support details](#bk_support)

```
file
```


## Members


**Properties**


|**Name**|**Description**|
|:-----|:-----|
|**[size](../reference/shared/file/size-property.md)**|Gets the document file size in bytes.|
|**[sliceCount](../reference/shared/file/slicecount-property.md)**|Gets the number of slices into which the file is divided.|

**Methods**


|**Name**|**Description**|
|:-----|:-----|
|**[closeAsync](../reference/shared/file/closeasync-method.md)**|Closes the document file.|
|**[getSliceAsync](../reference/shared/file/getsliceasync-method.md)**|Returns the specified slice.|

## Remarks

Access the  **File** object with the[AsyncResult.value](../reference/shared/asyncresult/value-property.md) property in the callback function passed to the[Document.getFileAsync](../reference/shared/document/getfileasync-method.md) method.


## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this object is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this object.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


|||||
|:-----|:-----|:-----|:-----|
||Office for Windows desktop|Office Online(in browser)|Office for iPad|
|**PowerPoint**|Y|Y|Y|
|**Word**|Y||Y|

|||
|:-----|:-----|
|**Available in requirement set**|File|
|**Add-in types**|Content, task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.1|Added support for PowerPoint and Word in Office for iPad.|
|1.0|Introduced|
