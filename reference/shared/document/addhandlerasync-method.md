
# Document.addHandlerAsync method (JavaScript API for Office)
Adds an event handler for a  **Document** object event.

|||
|:-----|:-----|
|**Hosts:**|Excel, PowerPoint, Project, Word|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|DocumentEvents|
|**[Added](#bk_history) in**|1.1|
[See all support details](#bk_support)

[![Try out this call in the interactive API Tutorial for Excel](../images/819b84bf-151c-4a12-80c3-d6f8d7c03251.png)](http://officeapitutorial.azurewebsites.net/Redirect.mdl?scenario=Selection+Changed)


```
Office.context.document.addHandlerAsync(eventType, handler  [, options], callback);
```


## Parameters



|**Name**|**Type**|**Description**|**Support notes**|
|:-----|:-----|:-----|:-----|
| _eventType_|[EventType](../reference/enumerations/eventtype-enumeration.md)|For a  **Document** object event, the _eventType_ parameter can be specified as **Office.EventType.DocumentSelectionChanged**, or the corresponding text value of this enumeration.||
| _handler_|**object**|The event handler function to add, whose only parameter is of type [DocumentSelectionChangedEventArgs](../reference/shared/document/selectionchangedeventargs-object/documentselectionchangedeventargs-object.md). Required.||
|||||
| _options_|**object**|Specifies any of the following [optional parameters](http://msdn.microsoft.com/library/7fe6bb42-3178-4d96-85f5-af5caea7b950%28Office.15%29.aspx#AsyncProgramming_OptionalParameters):||
| _asyncContext_|**array**,  **boolean**,  **null**,  **number**,  **object**, **string**, or  **undefined**|A user-defined item of any type that is returned in the  **AsyncResult** object without being altered.||
| _callback_|**object**|A function that is invoked when the callback returns, whose only parameter is of type  **AsyncResult**.||

## Callback Value

When the function you passed to the  _callback_ parameter executes, it receives an[AsyncResult](../reference/shared/asyncresult-object.md) object that you can access from the callback function's only parameter.

In the callback function passed to the  **addHandlerAsync** method, you can use the properties of the **AsyncResult** object to return the following information.



|**Property**|**Use to...**|
|:-----|:-----|
|[AsyncResult.value](../reference/shared/asyncresult/value-property.md)|Always returns  **undefined** because there is no data or object to retrieve when adding an event handler.|
|[AsyncResult.status](../reference/shared/asyncresult/status-property.md)|Determine the success or failure of the operation.|
|[AsyncResult.error](../reference/shared/asyncresult/error-property.md)|Access an [Error](../reference/shared/error/error-object.md) object that provides error information if the operation failed.|
|[AsyncResult.asyncContext](../reference/shared/asyncresult/asynccontext-property.md)|Access your user-defined  **object** or value, if you passed one as the _asyncContext_ parameter.|

## Remarks

You can add multiple event handlers for the specified  _eventType_ as long as the name of each event handler function is unique.


## Example




```
function addSelectionChangedEventHandler() {
    Office.context.document.addHandlerAsync(Office.EventType.DocumentSelectionChanged, MyHandler);
}

function MyHandler(eventArgs) {
    write('Event raised: ' + eventArgs.type);
    doSomethingWithDocument(eventArgs.document);
}

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```




## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this method is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this method.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


**Supported hosts, by platform**


||**Office for Windows desktop**|**Office Online(in browser)**|**Office for iPad**|
|:-----|:-----|:-----|:-----|
|**Excel**|Y|Y|Y|
|**PowerPoint**|Y|Y|Y|
|**Project**|Y|||
|**Word**|Y|Y|Y|

|||
|:-----|:-----|
|**Available in requirement sets**|DocumentEvents|
|**Minimum permission level**|[ReadWriteDocument](http://msdn.microsoft.com/library/da2efadc-4ebf-45fe-be39-397ac1eb1dbd%28Office.15%29.aspx)|
|**Add-in types**|Content, task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.1|Added support for Excel, PowerPoint, and Word in Office for iPad.|
|1.0|Introduced|
