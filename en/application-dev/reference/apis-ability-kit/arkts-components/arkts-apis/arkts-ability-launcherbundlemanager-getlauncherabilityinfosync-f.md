# getLauncherAbilityInfoSync

## Modules to Import

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## getLauncherAbilityInfoSync

```TypeScript
function getLauncherAbilityInfoSync(bundleName: string, userId: number): Array<LauncherAbilityInfo>
```

Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) based on the given bundle name and user ID.

**Since:** 18

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md)&gt; | Array of the [LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md) objects obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Verify permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |

**Examples**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let launcherAbilityInfos = launcherBundleManager.getLauncherAbilityInfoSync("com.example.demo", 100);
  console.info("data is " + JSON.stringify(launcherAbilityInfos));
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
