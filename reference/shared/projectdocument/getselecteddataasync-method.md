
# ProjectDocument.getSelectedDataAsync method (JavaScript API for Office)
Asynchronously gets the text value of the data that is contained in the current selection of one or more cells in the Gantt Chart view.

|||
|:-----|:-----|
|**Hosts:**|Project|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|Selection|
|**[Added](#bk_history) in**|1.0|
[See all support details](#bk_support)

```
Office.context.document.getSelectedDataAsync(coercionType[, options][, callback]);
```


## Parameters



|**Name**|**Type**|**Description**|**Support notes**|
|:-----|:-----|:-----|:-----|
| _coercionType_|[CoercionType](../reference/enumerations/coerciontype-enumeration.md)|The type of data structure to return. Required.Project 2013 supports only  **Office.CoercionType.Text** or `"text"`.||
| _options_|**object**|Specifies any of the following [optional parameters](http://msdn.microsoft.com/library/7fe6bb42-3178-4d96-85f5-af5caea7b950%28Office.15%29.aspx#AsyncProgramming_OptionalParameters).||
| _valueFormat_|[ValueFormat](../reference/enumerations/valueformat-enumeration.md)|The formatting to use for number or date values. Project 2013 ignores this parameter and internally sets it to  `unformatted`.||
| _filterType_|[FilterType](../reference/enumerations/filtertype-enumeration.md)|Specifies whether to include only visible data or all data. Project 2013 ignores this parameter and internally sets it to  `all`.||
| _asyncContext_|**array**,  **boolean**,  **null**,  **number**,  **object**, **string**, or  **undefined**|A user-defined item of any type that is returned in the  **AsyncResult** object without being altered.||
| _callback_|**object**|A function that is invoked when the callback returns, whose only parameter is of type  **AsyncResult**.||

## Callback Value

When the  _callback_ function executes, it receives an[AsyncResult](../reference/shared/asyncresult-object.md) object that you can access from the parameter in the callback function.

For the  **getSelectedDataAsync** method, the returned[AsyncResult](../reference/shared/asyncresult-object.md) object contains the following properties.


****


|**Name**|**Description**|
|:-----|:-----|
|[asyncContext](../reference/shared/asyncresult/asynccontext-property.md)|The data that was passed in the optional  _asyncContext_ parameter, if the parameter was used.|
|[error](../reference/shared/asyncresult/error-property.md)|Information about the error, if the  **status** property equals **failed**.|
|[status](../reference/shared/asyncresult/status-property.md)|The  **succeeded** or **failed** status of the asynchronous call.|
|[value](../reference/shared/asyncresult/value-property.md)|The text value of the selected cells.|

## Remarks

The  **ProjectDocument.getSelectedDataAsync** method overrides the[Document.getSelectedDataAsync](../reference/shared/document/getselecteddataasync-method.md) method and returns the text value of data that is selected in one or more cells in the Gantt Chart view. **ProjectDocument.getSelectedDataAsync** supports only a text format as the[CoercionType](../reference/enumerations/coerciontype-enumeration.md)—it does not support  `matrix`,  `table`, or other formats.


## Example

The following code example gets the values of the selected cells. It uses the optional  _asyncContext_ parameter to pass some text to the callback function.

The example assumes your add-in has a reference to the jQuery library and that the following page controls are defined in the content div in the page body.




```HTML
<input id="get-info" type="button" value="Get info" /><br />
<span id="message"></span>
```




```
(function () {
    "use strict";

    // The initialize function must be run each time a new page is loaded.
    Office.initialize = function (reason) {
        $(document).ready(function () {

            // After the DOM is loaded, add-in-specific code can run.
            $('#get-info').click(getSelectedText);
        });
    };

    // Get the text from the selected cells in the document, and display it in the add-in.
    function getSelectedText() {
        Office.context.document.getSelectedDataAsync(
            Office.CoercionType.Text,
            {asyncContext: 'Some related info'},
            function (result) {
                if (result.status === Office.AsyncResultStatus.Failed) {
                    onError(result.error);
                }
                else {
                    var output = String.format(
                        'Selected text: {0}<br/>Passed info: {1}',
                        result.value, result.asyncContext);
                    $('#message').html(output);
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
|**Available in requirement sets**|Selection|
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
[Office.CoercionType](../reference/enumerations/coerciontype-enumeration.md)
[ProjectDocument object](../reference/shared/projectdocument/projectdocument-object.md)
