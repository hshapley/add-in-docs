
# ProjectDocument.getWSSUrlAsync method (JavaScript API for Office)
Asynchronously gets the URL of the synchronized SharePoint task list.

|||
|:-----|:-----|
|**Hosts:**|Project|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|Selection|
|**[Added](#bk_history) in**|1.0|
[See all support details](#bk_support)

```
Office.context.document.getWSSUrlAsync([options,] [callback]);
```


## Parameters



|**Name**|**Type**|**Description**|**Support notes**|
|:-----|:-----|:-----|:-----|
| _options_|**object**|Specifies any of the following [optional parameters](http://msdn.microsoft.com/library/7fe6bb42-3178-4d96-85f5-af5caea7b950%28Office.15%29.aspx#AsyncProgramming_OptionalParameters).||
| _asyncContext_|**array**,  **boolean**,  **null**,  **number**,  **object**, **string**, or  **undefined**|A user-defined item of any type that is returned in the  **AsyncResult** object without being altered.||
| _callback_|**object**|A function that is invoked when the callback returns, whose only parameter is of type  **AsyncResult**.||

## Callback Value

When the  _callback_ function executes, it receives an[AsyncResult](../reference/shared/asyncresult-object.md) object that you can access from the parameter in the callback function.

For the  **getWSSUrlAsync** method, the returned[AsyncResult](../reference/shared/asyncresult-object.md) object contains following properties.


****


|**Name**|**Description**|
|:-----|:-----|
|[asyncContext](../reference/shared/asyncresult/asynccontext-property.md)|The data passed in the optional  _asyncContext_ parameter, if the parameter was used.|
|[error](../reference/shared/asyncresult/error-property.md)|Information about the error, if the  **status** property equals **failed**.|
|[status](../reference/shared/asyncresult/status-property.md)|The  **succeeded** or **failed** status of the asynchronous call.|
|[value](../reference/shared/asyncresult/value-property.md)|Contains the following properties:
<ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:MSHelp="http://msdn.microsoft.com/mshelp" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>The <span class="keyword">listName</span> property is the name of the synchronized SharePoint task list.</p></li><li><p>The <span class="keyword">serverUrl</span> property is the URL of the synchronized SharePoint task list.</p></li></ul>|

## Remarks

If the active project is not synchronized with a SharePoint task list, the  **listName** and **serverUrl** values are empty.


## Example

The following code example calls  **getWSSUrlAsync** to get the name and URL of the synchronized SharePoint task list.

The example assumes your add-in has a reference to the jQuery library and that the following page control is defined in the content div in the page body.




```HTML
<span id="message"></span>
```




```
(function () {
    "use strict";

    // The initialize function must be run each time a new page is loaded.
    Office.initialize = function (reason) {
        $(document).ready(function () {

            // After the DOM is loaded, add-in-specific code can run.
            getSharePointTaskListUrl();
        });
    };

    // Get the URL of the the synchronized SharePoint task list.
    function getSharePointTaskListUrl() {
        Office.context.document.getWSSUrlAsync(
            function (result) {
                if (result.status === Office.AsyncResultStatus.Succeeded) {
                    var output = String.format(
                        'List name: {0}<br />List URL: {1}',
                        result.value.listName, result.value.serverUrl);
                    $('#message').html(output);
                }
                else {
                    onError(result.error);
                }
            }
        );
    }

    function onError(error) {
        $('#message').html(error.name + ' ' + error.code + ': ' + error.message);
    }
})();
```


## Support details
<a name="bk_support"> </a>

A capital Y in the following matrix indicates that this method is supported in the corresponding Office host application. An empty cell indicates that the Office host application doesn't support this method.

For more information about Office host application and server requirements, see [Requirements for running Office Add-ins](http://msdn.microsoft.com/library/67340567-bb9a-498c-96d3-3f52f28c16bc%28Office.15%29.aspx).


|
|
||**Office for Windows desktop**|**Office Online(in browser)**|
|:-----|:-----|:-----|
|**Project**|Y||

|||
|:-----|:-----|
|**Available in requirement sets**||
|**Minimum permission level**|[ReadDocument](http://msdn.microsoft.com/library/da2efadc-4ebf-45fe-be39-397ac1eb1dbd%28Office.15%29.aspx)|
|**Add-in types**|Task pane|
|**Library**|Office.js|
|**Namespace**|Office|

## Support history
<a name="bk_history"> </a>


****


|**Version**|**Changes**|
|:-----|:-----|
|1.0|Introduced|

## See also
<a name="bk_history"> </a>


#### Other resources


[AsyncResult object](../reference/shared/asyncresult-object.md)
[ProjectDocument object](../reference/shared/projectdocument/projectdocument-object.md)
