# getAppCloneIdentity

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAppCloneIdentity

```TypeScript
function getAppCloneIdentity(uid: number): Promise<AppCloneIdentity>
```

Obtains the bundle name and clone index of a cloned application based on the given UID. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | UID of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AppCloneIdentity](arkts-ability-bundlemanager-appcloneidentity-t.md)&gt; | Promise used to return the application clone index. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700021](../errorcode-bundle.md#17700021-invalid-uid) | The uid is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005;

try {
  bundleManager.getAppCloneIdentity(uid).then((res) => {
    hilog.info(0x0000, 'testTag', 'getAppCloneIdentity res = %{public}s', JSON.stringify(res));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', message);
}
```
