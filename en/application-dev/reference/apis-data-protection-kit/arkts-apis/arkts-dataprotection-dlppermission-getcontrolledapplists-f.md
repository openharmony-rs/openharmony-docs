# getControlledAppLists

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getControlledAppLists

```TypeScript
function getControlledAppLists(): Promise<Array<string>>
```

Obtains the list of applications controlled by enterprise DLP for the current user. This API uses a promise to return the result.

> **NOTE:** 
> This API can only be used to query the list of applications controlled by enterprise DLP, which is set using
> [setControlledAppLists](arkts-dataprotection-dlppermission-setcontrolledapplists-f.md).

**Since:** 26.0.0

**Required permissions:** ohos.permission.DLP_POLICY_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of applications controlled by enterprise DLP for the current user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getControlledAppLists().then((res) => {
  console.info('res', JSON.stringify(res));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
}).finally(() => {
  console.info("Completed getControlledAppLists operation.");
})
```
