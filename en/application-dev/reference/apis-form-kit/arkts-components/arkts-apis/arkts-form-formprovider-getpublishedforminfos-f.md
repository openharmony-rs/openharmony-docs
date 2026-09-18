# getPublishedFormInfos

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getPublishedFormInfos

```TypeScript
function getPublishedFormInfos(): Promise<Array<formInfo.FormInfo>>
```

Obtains the information of all widgets that have been added to the home screen on the device. This API uses a promise to return the result.

> **NOTE:** 
> 
> This field is supported since API version 18 and deprecated since API version 20. You are advised to use
> [getPublishedRunningFormInfos](arkts-form-formprovider-getpublishedrunningforminfos-f.md) instead.

**Since:** 18

**Deprecated since:** 20

**Substitutes:** [getPublishedRunningFormInfos](arkts-form-formprovider-getpublishedrunningforminfos-f.md)

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.Form

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[formInfo.FormInfo](arkts-form-forminfo-forminfo-i.md)&gt;&gt; | Promise used to return the information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

**Examples**

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getPublishedFormInfos().then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getPublishedFormInfos, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
