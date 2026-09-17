# getExtensionAbilityResourceInfo (System API)

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getExtensionAbilityResourceInfo

```TypeScript
function getExtensionAbilityResourceInfo(bundleName: string, extensionAbilityType: bundleManager.ExtensionAbilityType, resourceFlags: number, appIndex?: number): Array<LauncherAbilityResourceInfo>
```

Obtains the ExtensionAbility resource information of an application based on the bundle name, ExtensionAbility type, resource flags, and clone ID. This API returns the result synchronously.

**Since:** 20

**Required permissions:** ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| extensionAbilityType | [bundleManager.ExtensionAbilityType](arkts-ability-bundlemanager-extensionabilitytype-e.md) | Yes | ExtensionAbility type. Only **ExtensionAbilityType.INPUT_METHOD**, **ExtensionAbilityType.SHARE** and **ExtensionAbilityType.ACTION** are supported. |
| resourceFlags | number | Yes | Resource information flags, which indicate the type of resource information to obtain. |
| appIndex | number | No | ID of the application clone. The default value is **0**. The value ranges from 0 to 5. The value **0** indicates the main application. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt; | ExtensionAbility resource information of the application, including the icon and name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range or not found. |

**Examples**

```TypeScript
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "com.example.myapplication";
let extensionAbilityType = bundleManager.ExtensionAbilityType.INPUT_METHOD;
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo =
    bundleResourceManager.getExtensionAbilityResourceInfo(bundleName, extensionAbilityType, resourceFlag);
  console.info('getExtensionAbilityResourceInfo successfully. Data label: ' + JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  let code = (err as BusinessError).code;
  console.error(`getExtensionAbilityResourceInfo failed, err code:${code}, err msg: ${message}`);
}
```
