# getFormRect

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getFormRect

```TypeScript
function getFormRect(formId: string): Promise<formInfo.Rect>
```

Obtains the position and dimension of a widget. This API uses a promise to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | Promise used to return the position and dimension of the widget relative to the upper-left corner of the screen, in vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.function getFormRect cannot work correctly due to limited device capabilities. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501001](../errorcode-form.md#16501001-widget-id-not-exist) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-widget-not-operatable) | The form cannot be operated by the current application. |

**Examples**

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.

try {
  formProvider.getFormRect(formId).then((data: formInfo.Rect) => {
    console.info(`getFormRect succeed, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
