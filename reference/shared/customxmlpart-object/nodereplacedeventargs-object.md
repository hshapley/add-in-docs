
# NodeReplacedEventArgs object (JavaScript API for Office)
Provides information about the replaced node that raised the [nodeReplaced](../reference/shared/customxmlpart-object/nodereplaced-event.md) event.

|||
|:-----|:-----|
|**Hosts:**|Word|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|CustomXmlParts|
|**[Last changed](#bk_history) in**|1.1|
[See all support details](#bk_support)

```
NodeReplacedEventArgs
```


## Members


**Properties**


|**Name**|**Description**|
|:-----|:-----|
|[isUndoRedo](../reference/shared/customxmlpart-object/isundoredo-property.md)|Gets whether the replaced node was inserted as part of an undo or redo operation by the user.|
|[newNode](../reference/shared/customxmlpart-object/newnode-property.md)|Gets the new node.|
|[oldNode](../reference/shared/customxmlpart-object/oldnode-property.md)|Gets the old (replaced) node.|

## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this object is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this object.

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
