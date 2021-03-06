
# ProjectDocument.getResourceFieldAsync method (JavaScript API for Office)
Asynchronously gets the value of the specified field for the specified resource in a resource view.

|||
|:-----|:-----|
|**Hosts:**|Project|
|**Available in [Requirement set](http://msdn.microsoft.com/library/6b6702f2-b0a5-46ab-a356-8dda897ca8ae%28Office.15%29.aspx)**|Selection|
|**[Added](#bk_history) in**|1.0|
[See all support details](#bk_support)

```
Office.context.document.getResourceFieldAsync(resourceId, fieldId[, options][, callback]);
```


## Parameters



|**Name**|**Type**|**Description**|**Support notes**|
|:-----|:-----|:-----|:-----|
| _resourceId_|**string**|The GUID of the resource. Required.||
| _fieldId_|[ProjectResourceFields](../reference/enumerations/projectresourcefields-enumeration.md)|The ID of the target field. Required.||
| _options_|**object**|Specifies any of the following [optional parameters](http://msdn.microsoft.com/library/7fe6bb42-3178-4d96-85f5-af5caea7b950%28Office.15%29.aspx#AsyncProgramming_OptionalParameters).||
| _asyncContext_|**array**,  **boolean**,  **null**,  **number**,  **object**, **string**, or  **undefined**|A user-defined item of any type that is returned in the  **AsyncResult** object without being altered.||
| _callback_|**object**|A function that is invoked when the callback returns, whose only parameter is of type  **AsyncResult**.||

## Callback Value

When the  _callback_ function executes, it receives an[AsyncResult](../reference/shared/asyncresult-object.md) object that you can access from the parameter in the callback function.

For the  **getResourceFieldAsync** method, the returned[AsyncResult](../reference/shared/asyncresult-object.md) object contains the following properties.


****


|**Name**|**Description**|
|:-----|:-----|
|[asyncContext](../reference/shared/asyncresult/asynccontext-property.md)|The data passed in the optional  _asyncContext_ parameter, if the parameter was used.|
|[error](../reference/shared/asyncresult/error-property.md)|Information about the error, if the  **status** property equals **failed**.|
|[status](../reference/shared/asyncresult/status-property.md)|The  **succeeded** or **failed** status of the asynchronous call.|
|[value](../reference/shared/asyncresult/value-property.md)|Contains the  **fieldValue** property, which represents the value of the specified field.|

## Remarks

First call the [getSelectedResourceAsync](../reference/shared/projectdocument/getselectedtaskasync-method.md) method to get the resource GUID, and then pass it as the _resourceId_ argument to **getResourceFieldAsync**. If the active view is not a resource view (for example a Resource Usage or Resource Sheet view), or if no resource is selected in a resource view, [getSelectedResourceAsync](../reference/shared/projectdocument/getselectedtaskasync-method.md) returns a 5001 error (Internal Error). See[addHandlerAsync method](../reference/shared/projectdocument/addhandlerasync-method.md) for an example that uses the[ViewSelectionChanged](../reference/shared/projectdocument/viewselectionchanged-event.md) event and the[getSelectedViewAsync](../reference/shared/projectdocument/getselectedviewasync-method.md) method to activate a button based on the active view type.


## Example

The following code example calls [getSelectedResourceAsync](../reference/shared/projectdocument/getselectedtaskasync-method.md) to get the GUID of the resource that's currently selected in a resource view. Then it gets three resource field values by calling **getResourceFieldAsync** recursively.

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
            $('#get-info').click(getResourceInfo);
        });
    };

    // Get the GUID of the resource and then get the resource fields.
    function getResourceInfo() {
        getResourceGuid().then(
            function (data) {
                getResourceFields(data);
            }
        );
    }

    // Get the GUID of the selected resource.
    function getResourceGuid() {
        var defer = $.Deferred();
        Office.context.document.getSelectedResourceAsync(
            function (result) {
                if (result.status === Office.AsyncResultStatus.Failed) {
                    onError(result.error);
                }
                else {
                    defer.resolve(result.value);
                }
            }
        );
        return defer.promise();
    }

    // Get the specified fields for the selected resource.
    function getResourceFields(resourceGuid) {
        var targetFields =
            [Office.ProjectResourceFields.Name, Office.ProjectResourceFields.Units, Office.ProjectResourceFields.BaseCalendar];
        var fieldValues = ['Name: ', 'Units: ', 'Base calendar: '];
        var index = 0; 
        getField();

        // Get each field, and then display the field values in the add-in.
        function getField() {
            if (index == targetFields.length) {
                var output = '';
                for (var i = 0; i < fieldValues.length; i++) {
                    output += fieldValues[i] + '<br />';
                }
                $('#message').html(output);
            }

            // If the call is successful, get the field value and then get the next field.
            else {
                Office.context.document.getResourceFieldAsync(
                    resourceGuid,
                    targetFields[index],
                    function (result) {
                        if (result.status === Office.AsyncResultStatus.Succeeded) {
                            fieldValues[index] += result.value.fieldValue;
                            getField(index++);
                        }
                        else {
                            onError(result.error);
                        }
                    }
                );
            }
        }
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


[getSelectedResourceAsync method](../reference/shared/projectdocument/getselectedresourceasync-method.md)
[ProjectResourceFields enumeration](../reference/enumerations/projectresourcefields-enumeration.md)
[AsyncResult object](../reference/shared/asyncresult-object.md)
[ProjectDocument object](../reference/shared/projectdocument/projectdocument-object.md)
