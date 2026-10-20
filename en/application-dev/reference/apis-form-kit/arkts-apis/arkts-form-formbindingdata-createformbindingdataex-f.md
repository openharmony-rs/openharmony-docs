# createFormBindingDataEx

## Modules to Import

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## createFormBindingDataEx

```TypeScript
function createFormBindingDataEx(obj?: Object | string): FormBindingData
```

Creates a **FormBindingData** object.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-formBindingData-function createFormBindingDataEx(obj?: Object | string): FormBindingData--><!--Device-formBindingData-function createFormBindingDataEx(obj?: Object | string): FormBindingData-End-->

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object &#124; string | No | Data to be displayed on the widget. The value can be an object containing multiple key-value pairs or a JSON string. The image data is identified by **'formImages'**, and the content is multiple key-value pairs, each of which consists of an image identifier and image file descriptor. The final format is {'formImages': {'key1': fd1, 'key2': fd2}}.<br>**NOTE:** <br>During [widget update](../../../form/arkts-ui-widget-interaction-overview.md), when the widget UI receives widget data through @LocalStorageProp, the **FormBindingData** object is serialized, that is, the widget data is converted into the string type. if the widget data is updated using shared memory, the total size of the updated data cannot exceed 10 MB, the number of updated images cannot exceed 30.Exceeding the limit will result in abnormal display. |

**Return value:**

| Type | Description |
| --- | --- |
| [FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | **FormBindingData** object created based on the passed data. |
