# getFormIdsByFormLocation (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## getFormIdsByFormLocation

```TypeScript
function getFormIdsByFormLocation(location: formInfo.FormLocation): Promise<Array<string>>
```

Obtains the list of widget IDs at a specified location on the device. This API uses a promise to return the result.

**Since:** 24

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [formInfo.FormLocation](arkts-form-forminfo-formlocation-e.md) | Yes | Widget location. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the obtained widget ID list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501016](../errorcode-form.md#16501016-invalid-widget-location-information) | The location of the widget is invalid. |

**Examples**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.getFormIdsByFormLocation(formInfo.FormLocation.DESKTOP).then((formIds: Array<string>) => {
    console.info('formHost getFormIdsByFormLocation success.');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```
