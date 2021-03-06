
# CustomXmlNode object (JavaScript API for Office)
Represents an XML node in a tree in a document.

|||
|:-----|:-----|
|**Hosts:**|Word|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|CustomXmlParts|
|**[Last changed](#bk_history) in**|1.1|
[See all support details](#bk_support)

```
CustomXmlNode
```


## Members


**Properties**


|**Name**|**Description**|
|:-----|:-----|
|[baseName](../reference/shared/customxmlnode-object/basename-property.md)|Gets the base name of the node without the namespace prefix, if one exists.|
|[nodeType](../reference/shared/customxmlnode-object/nodetype-property.md)|Gets the type of the  **CustomXMLNode**.|
|[namespaceUri](../reference/shared/customxmlnode-object/namespaceuri-property.md)|Retrieves the string GUID of the  **CustomXMLPart**.|

**Methods**


|**Name**|**Description**|
|:-----|:-----|
|[getNodesAsync](../reference/shared/customxmlnode-object/getnodesasync-method.md)|Asynchronously gets the nodes as an array of  **CustomXMLNode** objects matching the relative XPath expression.|
|[getNodeValueAsync](../reference/shared/customxmlnode-object/getnodevalueasync-method.md)|Asynchronously gets the value of the node.|
|[getXmlAsync](../reference/shared/customxmlnode-object/getxmlasync-method.md)|Asynchronously gets the XML of the node.|
|[setNodeValueAsync](../reference/shared/customxmlnode-object/setnodevalueasync-method.md)|Asynchronously sets the value of the node.|
|[setXmlAsync](../reference/shared/customxmlnode-object/setxmlasync-method.md)|Asynchronously sets the XML of the node.|

## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this method is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this method.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


|
|
||**Office for Windows desktop**|**Office Online(in browser)**|**Office for iPad**|
|:-----|:-----|:-----|:-----|
|**Word**|Y||Y|

|||
|:-----|:-----|
|**Available in requirement sets**|CustomXmlParts|
|**Minimum permission level**|[ReadWriteDocument](http://msdn.microsoft.com/library/da2efadc-4ebf-45fe-be39-397ac1eb1dbd%28Office.15%29.aspx)|
|**Add-in types**|Task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.1|Added support for Word in Office for iPad.|
|1.0|Introduced|
